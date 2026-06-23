
<!-- ════════════════════ CONTACT & BOOKING ════════════════════ -->
<section id="contact" class="section-contact">
  <div class="wrap">

    <div class="sh center" style="--sh-accent: var(--ssso-red);">
      <div class="sh-eyebrow">let&rsquo;s make something</div>
      <h2 class="sh-title">Contact &amp; Booking<span class="sh-bar"></span></h2>
    </div>
    <p style="text-align:center; font-size:17px; line-height:1.6; color:var(--text-body); max-width:52ch; margin:16px auto 36px;">
      Workshops, keynotes, cohort partnerships, or just a good idea — drop a note and Shelly will get back to you.
    </p>

    <div class="contact-grid">

      <!-- Form card -->
      <div class="card p-lg">
        <form class="contact-form" id="contact-form" novalidate>
          <div class="form-row-2">
            <div class="field">
              <label class="field-label" for="f-name">Your name</label>
              <input class="field-input" type="text"  id="f-name"   placeholder="Shelly Veron"   required />
            </div>
            <div class="field">
              <label class="field-label" for="f-email">Email</label>
              <input class="field-input" type="email" id="f-email"  placeholder="you@school.org" required />
            </div>
          </div>
          <div class="field">
            <label class="field-label" for="f-school">School / District</label>
            <input class="field-input" type="text" id="f-school" placeholder="Bright Mind Academy" />
          </div>
          <div class="field">
            <label class="field-label" for="f-msg">What do you need?</label>
            <textarea class="field-input field-textarea" id="f-msg" rows="4" placeholder="Tell me about your event or cohort…"></textarea>
          </div>
          <button type="submit" class="btn btn-primary lg">Send it 🚀</button>
        </form>

        <div class="contact-success" id="contact-success" role="status" aria-live="polite">
          <div class="success-title">You&rsquo;re in! 🎉</div>
          <p class="success-msg">Shelly said so — we&rsquo;ll be in touch shortly.</p>
          <button class="btn btn-secondary" style="margin-top:14px;" id="btn-reset">Send another</button>
        </div>
      </div>

      <!-- Contact info -->
      <div class="contact-info">
        <div class="card p-sm">
          <span class="card-stripe" style="background: var(--ssso-red);"></span>
          <div class="card-body">
            <div class="contact-info-label">Email</div>
            <div class="contact-info-value">shellysaidsoedu@gmail.com</div>
          </div>
        </div>
        <div class="card p-sm">
          <span class="card-stripe" style="background: var(--ssso-red);"></span>
          <div class="card-body">
            <div class="contact-info-label">Phone</div>
            <div class="contact-info-value">281-796-0187</div>
          </div>
        </div>
        <div class="card p-sm">
          <span class="card-stripe" style="background: var(--ssso-red);"></span>
          <div class="card-body">
            <div class="contact-info-label">Web</div>
            <div class="contact-info-value">www.shellysaidsoedu.com</div>
          </div>
        </div>
        <div class="contact-socials">
          <span class="badge badge-ink">𝕏 shelly_veron</span>
          <span class="badge badge-ink">in shellyveron</span>
          <span class="badge badge-ink">◉ shellysaidsoedu</span>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- ════════════════════ FOOTER ════════════════════ -->
<footer class="site-footer">
  <div class="footer-inner">
    <img class="footer-wordmark" src="../../assets/ssso-wordmark.png" alt="Shelly Said So EDU" />
    <span class="footer-copy">© 2026 Shelly Said So EDU · A four-brand creative + educational movement.</span>
  </div>
</footer>

<script>
(function () {
  'use strict';

  /* ── ACTIVE NAV (IntersectionObserver) ──────────────────── */
  var sectionIds = ['about', 'bright-minds', 'doom-closet', 'maker-index', 'contact'];
  var navLinks   = document.querySelectorAll('.nav-link');

  function setActive(id) {
    navLinks.forEach(function (a) {
      var match = a.getAttribute('data-nav') === id;
      a.classList.toggle('active', match);
    });
  }
  ReactDOM.createRoot(document.getElementById('root')).render(<App />);

  var observer = new IntersectionObserver(function (entries) {
    entries.forEach(function (entry) {
      if (entry.isIntersecting) setActive(entry.target.id);
    });
  }, { rootMargin: '-35% 0px -55% 0px' });

  sectionIds.forEach(function (id) {
    var el = document.getElementById(id);
    if (el) observer.observe(el);
  });

  /* ── CONTACT FORM ───────────────────────────────────────── */
  var form    = document.getElementById('contact-form');
  var success = document.getElementById('contact-success');
  var reset   = document.getElementById('btn-reset');

  form.addEventListener('submit', function (e) {
    e.preventDefault();
    /* Basic validation */
    var name  = document.getElementById('f-name').value.trim();
    var email = document.getElementById('f-email').value.trim();
    if (!name || !email) return;
    form.style.display    = 'none';
    success.style.display = 'block';
  });

  reset.addEventListener('click', function () {
    success.style.display = 'none';
    form.style.display    = 'flex';
    form.reset();
  });

  /* ── CARD HOVER (interactive) ───────────────────────────── */
  document.querySelectorAll('.card.interactive').forEach(function (card) {
    card.addEventListener('mouseenter', function () {
      card.style.transform  = 'translate(-2px,-2px)';
      card.style.boxShadow  = 'var(--shadow-pop-lg)';
    });
    card.addEventListener('mouseleave', function () {
      card.style.transform  = '';
      card.style.boxShadow  = 'var(--shadow-pop)';
    });
  });

  /* ── BUTTON PRESS EFFECT ────────────────────────────────── */
  document.querySelectorAll('.btn:not(.btn-secondary)').forEach(function (btn) {
    btn.addEventListener('mousedown', function () {
      btn.style.transform  = 'translate(4px,4px)';
      btn.style.boxShadow  = '1px 1px 0 var(--ink)';
    });
    var up = function () {
      btn.style.transform  = '';
      btn.style.boxShadow  = '';
    };
    btn.addEventListener('mouseup',    up);
    btn.addEventListener('mouseleave', up);
  });

}());
</script>
</body>
</html>
