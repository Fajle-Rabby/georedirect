addEventListener('fetch', event => {
  event.respondWith(handleRequest(event.request));
});

async function handleRequest(request) {
  const country = request.headers.get('CF-IPCountry'); // Cloudflare এর মাধ্যমে দেশের কোড চেক
  const host = request.headers.get('host'); // হোস্ট ডোমেইন চেক

  // বাংলাদেশ থেকে TechMartIT.com এ ঢুকলে TechMart.com.bd এ রিডিরেক্ট করুন
  if (country === 'BD' && host === 'techmartit.com') {
    return Response.redirect('https://techmart.com.bd', 301);
  }

  // বাংলাদেশের বাইরে থেকে TechMart.com.bd এ ঢুকলে TechMartIT.com এ রিডিরেক্ট করুন
  if (country !== 'BD' && host === 'techmart.com.bd') {
    return Response.redirect('https://techmartit.com', 301);
  }

  // অন্যসব ক্ষেত্রে ওয়েবসাইট স্বাভাবিকভাবে লোড হতে দিন
  return fetch(request);
}
