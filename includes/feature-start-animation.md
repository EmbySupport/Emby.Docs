
# Startup Animation

<video src="../../../videos/EmbyStartAnimFlat.mp4" controls="controls" style="max-height:640px; min-height: 200px; max-width: 100%;">
</video>

## Why it Exists

It had turned out that it takes a number of seconds until the web app environment is initialized and ready for the actual startup process which takes another few seconds until the app is ready for use. This cannot be accelerated, so the only option was to cover that time span with something visual. Showing a spinner is always the worst option for those situations because it doesn't provide any indication about progress, so you're unable to see how much time is still remaining (that's why spinners are typically used for cases when the duration is unknown).
A progress bar can be followed and indicates the remaining amount of time, but too often those are used in a way that progress stops at 90 or 95% for much longer than it should, so nobody trusts them anymore these days.
The start animation in turn has a fixed duration and once it's finished, the app is (almost, like 99.9%) guaranteed to be ready. The predictability of it makes it subjectively feel faster than a spinner or a static logo display.

