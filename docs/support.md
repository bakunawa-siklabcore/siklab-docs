# Get Help

Most questions have a published answer. Ask below and you'll get it straight away — if there isn't
one, the form will help you send a message that we can actually act on.

<div id="siklab-support">

<div class="sk-step">
  <label for="sk-q"><strong>What do you need help with?</strong></label>
  <input id="sk-q" type="text" autocomplete="off"
         placeholder="e.g. does it run on Windows?  ·  how do I cancel?  ·  my build is stuck" />
  <button id="sk-ask" type="button">Check for an answer</button>
</div>

<div id="sk-answer" hidden></div>

<div id="sk-form" hidden>
  <hr>
  <p><strong>Still need a person?</strong> Pick what this is about — it changes what's useful to
  include, and a message with the right details gets a real answer instead of a round of questions.</p>

  <label for="sk-kind">This is about</label>
  <select id="sk-kind">
    <option value="">— choose —</option>
    <option value="presale">A question before I buy</option>
    <option value="billing">Billing, a refund, or cancelling</option>
    <option value="licence">My licence or activation</option>
    <option value="bug">Something is broken</option>
    <option value="security">A security issue</option>
  </select>

  <div id="sk-fields"></div>

  <div id="sk-warn" hidden></div>

  <button id="sk-send" type="button" disabled>Compose the email</button>
  <p class="sk-note">This opens your own email app with the message filled in. Nothing is sent
  anywhere until you press send, and you can read and edit every word of it first.</p>
</div>

</div>

<style>
#siklab-support input[type=text], #siklab-support select, #siklab-support textarea {
  width: 100%; padding: .6rem .7rem; margin: .3rem 0 .9rem; box-sizing: border-box;
  border: 1px solid var(--md-default-fg-color--lightest); border-radius: 6px;
  background: var(--md-default-bg-color); color: var(--md-default-fg-color); font: inherit;
}
#siklab-support textarea { min-height: 7rem; resize: vertical; }
#siklab-support button {
  padding: .55rem 1.1rem; border-radius: 6px; border: 0; cursor: pointer; font: inherit;
  font-weight: 600; background: var(--md-primary-fg-color); color: var(--md-primary-bg-color);
}
#siklab-support button:disabled { opacity: .45; cursor: not-allowed; }
#siklab-support .sk-note { font-size: .8rem; opacity: .75; margin-top: .5rem; }
#siklab-support .sk-card {
  border: 1px solid var(--md-default-fg-color--lightest); border-left: 3px solid var(--md-primary-fg-color);
  border-radius: 6px; padding: .9rem 1rem; margin: 1rem 0;
}
#siklab-support .sk-danger { border-left-color: #d32f2f; }
</style>

<script>
(function () {
  var API = 'https://siklab-broker.siklab-bakunawa.workers.dev/support/ask';
  var EMAIL = 'support@siklabcore.com';
  var SECURITY_EMAIL = 'security@siklabcore.com';

  // The SAME credential shapes the assistant refuses. Checked here too, because a form is where
  // someone is most likely to paste a key "so you can look at my account" — and a mailto: body is
  // the one place we could not scrub it afterwards.
  var SECRETS = [
    /sk-[a-zA-Z0-9_-]{8,}/, /sk_live_[a-zA-Z0-9]+/, /ghp_[a-zA-Z0-9]{16,}/,
    /xox[baprs]-[a-zA-Z0-9-]+/, /-----BEGIN [A-Z ]*PRIVATE KEY-----/,
    /AKIA[0-9A-Z]{16}/, /eyJ[a-zA-Z0-9_-]{10,}\.[a-zA-Z0-9_-]{10,}\./
  ];
  var hasSecret = function (s) { return SECRETS.some(function (re) { return re.test(s); }); };

  var $ = function (id) { return document.getElementById(id); };
  var esc = function (s) { return String(s).replace(/[&<>"]/g, function (c) {
    return ({ '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;' })[c]; }); };

  // Only what each kind of request actually needs. A pre-sale question does not need your version,
  // and a billing question does not need your OS — asking anyway is collecting for the sake of it.
  var FIELDS = {
    presale:  [['ctx', 'Anything that would help us answer (optional)', 'textarea']],
    billing:  [['ref', 'Order reference or the email you paid with', 'text'],
               ['ctx', 'What happened', 'textarea']],
    licence:  [['ref', 'The email you purchased with', 'text'],
               ['ctx', 'What you are seeing', 'textarea']],
    bug:      [['ver', 'Version (Settings → Updates)', 'text'],
               ['os',  'Operating system', 'text'],
               ['ctx', 'What you did, what you expected, what happened', 'textarea']],
    security: [['ctx', 'What you found, and how to reproduce it', 'textarea']],
  };

  function renderFields(kind) {
    var wrap = $('sk-fields');
    wrap.innerHTML = '';
    (FIELDS[kind] || []).forEach(function (f) {
      var id = 'sk-f-' + f[0];
      var el = f[2] === 'textarea' ? document.createElement('textarea') : document.createElement('input');
      if (f[2] !== 'textarea') el.type = 'text';
      el.id = id;
      var lab = document.createElement('label');
      lab.htmlFor = id; lab.textContent = f[1];
      wrap.appendChild(lab); wrap.appendChild(el);
      el.addEventListener('input', validate);
    });
    if (kind === 'security') {
      var n = document.createElement('div');
      n.className = 'sk-card';
      n.innerHTML = '<strong>Security reports go to a separate address</strong> (' + SECURITY_EMAIL +
        ') and we would rather hear about it early than not at all. Please do not include working ' +
        'credentials or customer data in the report.';
      wrap.appendChild(n);
    }
    validate();
  }

  function collected() {
    return (FIELDS[$('sk-kind').value] || []).map(function (f) {
      var el = $('sk-f-' + f[0]);
      return [f[1], el ? el.value.trim() : ''];
    });
  }

  function validate() {
    var kind = $('sk-kind').value;
    var vals = collected();
    var joined = vals.map(function (v) { return v[1]; }).join(' ') + ' ' + $('sk-q').value;
    var warn = $('sk-warn');

    if (hasSecret(joined)) {
      // BLOCK, do not merely warn. The whole point is that the credential never reaches the email.
      warn.hidden = false;
      warn.className = 'sk-card sk-danger';
      warn.innerHTML = '<strong>That looks like a key or token — please remove it.</strong> ' +
        'Nobody at Siklab will ever ask you for a key, a password or a licence file, and we cannot ' +
        'help faster by having one. If it was a real credential, rotate it with whoever issued it.';
      $('sk-send').disabled = true;
      return;
    }
    warn.hidden = true;

    // Enough to be actionable: a kind, and something written in the free-text box.
    var body = vals.length ? vals[vals.length - 1][1] : '';
    $('sk-send').disabled = !(kind && body.length > 10);
  }

  function compose() {
    var kind = $('sk-kind').value;
    var to = kind === 'security' ? SECURITY_EMAIL : EMAIL;
    var subjects = {
      presale: 'Question before buying', billing: 'Billing', licence: 'Licence',
      bug: 'Something is broken', security: 'Security report'
    };
    var lines = [];
    if ($('sk-q').value.trim()) lines.push('Asked: ' + $('sk-q').value.trim(), '');
    collected().forEach(function (v) { if (v[1]) lines.push(v[0] + ':', v[1], ''); });
    location.href = 'mailto:' + to +
      '?subject=' + encodeURIComponent('[' + (subjects[kind] || 'Support') + '] ') +
      '&body=' + encodeURIComponent(lines.join('\n'));
  }

  function ask() {
    var q = $('sk-q').value.trim();
    var out = $('sk-answer');
    if (!q) { $('sk-form').hidden = false; return; }

    out.hidden = false;
    out.className = 'sk-card';
    out.textContent = 'Checking…';

    fetch(API, {
      method: 'POST', headers: { 'content-type': 'application/json' },
      body: JSON.stringify({ question: q })
    }).then(function (r) { return r.json(); }).then(function (d) {
      out.className = (d.kind && d.kind.indexOf('refused') === 0) ? 'sk-card sk-danger' : 'sk-card';
      out.innerHTML = '<p>' + esc(d.answer) + '</p>' +
        (d.url ? '<p><a href="' + esc(d.url) + '">Read more</a></p>' : '');
      // A refusal is final — do not offer to email the same request to a person.
      $('sk-form').hidden = (d.kind === 'refused-secret-request' || d.kind === 'refused-secret-present');
    }).catch(function () {
      // The assistant being down must never block someone from reaching a human.
      out.className = 'sk-card';
      out.textContent = 'I could not check just now — the form below still works.';
      $('sk-form').hidden = false;
    });
  }

  $('sk-ask').addEventListener('click', ask);
  $('sk-q').addEventListener('keydown', function (e) { if (e.key === 'Enter') { e.preventDefault(); ask(); } });
  $('sk-q').addEventListener('input', validate);
  $('sk-kind').addEventListener('change', function () { renderFields(this.value); });
})();
</script>

---

## Or just email us

**[support@siklabcore.com](mailto:support@siklabcore.com)** — questions, billing, licences, anything.

**[security@siklabcore.com](mailto:security@siklabcore.com)** — security issues. We would rather hear
early than not at all.

Response target is **within 2 business days**, Philippine time (UTC+8). That is a goal, not a
contractual commitment — Siklab Core is run by one person, and it is more honest to say so than to
imply a support desk.

!!! danger "We will never ask you for a credential"
    Not an API key, not a password, not a licence key, not a private key, and not your customers'
    data. Anyone who does is not us. The form above blocks these on purpose.

---

## Before you write

Three pages answer most of what reaches us:

- **[Troubleshooting](troubleshooting.md)** — a build that looks stuck is usually the AI engine, not Siklab
- **[Questions](faq.md)** — buying, the trial, what leaves your machine, what you own
- **[Known Issues](known-issues.md)** — what is currently broken or unproven, published rather than left to be discovered

If you are inside the app, **Report a problem** in the top bar is faster than any of this — it
attaches your version and OS automatically.
