1. Gå til fork-en og riktig branch
cd /home/henrik/git/privat/zed
git checkout ai-credit-status-bar
2. Installer byggeavhengigheter (første gang)
På Linux:

script/linux
Dette installerer bl.a. cmake, X11/Wayland-biblioteker, libssl, clang m.m. Uten dette feiler bygget (f.eks. manglende x11.pc).

Nix: Du kan også bruke Zeds dev-shell:

nix develop
3. Bygg og start (raskeste for utvikling)
Debug-build (anbefalt første gang):

cargo run
Dette bygger og starter zed direkte fra crates/zed. Første bygg kan ta 15–30+ minutter.

Alternativt via CLI (nærmere release-oppsett):

cargo run -p cli
Raskere kjøring (etter første bygg):

cargo run --release
4. Installer lokalt (valgfritt)
Hvis du vil ha zed på PATH som vanlig installasjon:

./script/install-linux
Da får du ~/.local/bin/zed — start med:

~/.local/bin/zed
5. Verifiser AI-kreditt-funksjonen
I settings.json:

"ai_credit_status": {
  "enabled": true,
  "refresh_seconds": 60,
  "monthly_budget_usd": null
}
Indikatoren vises nederst til høyre i status bar når du har en aktiv AI-provider (Agent → default modell).

Vanlige problemer
Problem	Løsning
x11.pc / pkg-config feil
Kjør script/linux eller nix develop
Linker-feil med remote_server (GCC 14+)
export REMOTE_SERVER_TARGET=x86_64-unknown-linux-gnu før install
Wayland-problemer
Prøv WAYLAND_DISPLAY='' cargo run for X11
Langsomt første bygg
Normalt — bruk cargo run uten --release for raskere debug-bygg
Relaterte lenker
PR: https://github.com/zed-industries/zed/pull/59655
Offisiell Linux-dev-guide: docs/src/development/linux.md
Vil du at jeg skal prøve å bygge og starte den her i miljøet ditt, eller feilsøke en konkret byggefeil?