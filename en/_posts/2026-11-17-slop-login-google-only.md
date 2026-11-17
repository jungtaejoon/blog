---
title: "Why Google's sign-in page shows a strange Supabase address: rebuilding Slop's login"
description: How I cut Slop's login down to password and Google, put Kakao on hold, and added a note explaining the Supabase address Google shows during sign-in.
project: slop
ref: slop-login-google-only
kind: dev
image: https://slop.ai.kr/og.png
---

Three days after opening [Slop](https://slop.ai.kr/), I reworked the login screen. Most of the work was taking things out and explaining things, not adding features.

## I removed email-link sign-in

Having "sign in with a link sent to your email" next to password login kept raising the question "wait, which one did I use?" So I removed link sign-in and polished the password flow: show/hide password, a strength meter, a Caps Lock warning, and if you try to sign up with an email that already exists, you're sent to Log in.

## Kakao is on hold for now

I wanted every account tied to one email: someone who signed up with email and later uses a Google account with the same address lands in the same account. But a Kakao app (Kakao is the messaging app nearly everyone in Korea uses) registered by an individual can't get the user's email, so only Google is on for now. The buttons come from whichever providers are enabled in Supabase, so turning Kakao on later won't need a redeploy.

## Google shows an unfamiliar address

When I tried Google login myself, Google said I was continuing to an unfamiliar `xxxx.supabase.co`, not Slop. Google shows the address of the server that actually receives the sign-in. If it gave me pause as the builder, a first-time visitor would be even more uneasy.

So I added a short note next to the button. The first version just said "it's fine," and being told it's fine without a reason looks even more suspicious, so I fixed it the same day. Now it explains that Slop uses Supabase to manage accounts, and that your Google password never reaches Slop. All it gets is your name, email and profile photo.

## What I learned

More ways to sign in didn't make login friendlier. Fewer branches did, along with explaining up front wherever an unfamiliar screen is about to appear. Flip through a few cards on the [judge screen](https://slop.ai.kr/#/judge), and sign up if you like it. The code is on [GitHub](https://github.com/jungtaejoon/slop).
