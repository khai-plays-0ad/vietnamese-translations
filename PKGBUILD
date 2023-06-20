_0ad_patch=26
_0ad_ver=a$_0ad_patch
pkgname='0ad-vi-lang'
pkgver="0.0.$_0ad_patch"
pkgrel=1
pkgdesc='Vietnamese Translations for 0.A.D'
arch=(any)
url='https://github.com/khai-plays-0ad/vietnamese-translations.git'
license=('GPL')
optdepends=(
  "0ad=$_0ad_ver: The game"
  "0ad-data=$_0ad_ver: The data of the game"
)
makedepends=(
  'jq'
  'sed'
)
source=(
  'LICENSE'
  'mod.json'
  'for_use_0ad_engine_vi.po'
  'for_use_0ad_mod-selector_vi.po'
  'for_use_0ad_public-civilizations_vi.po'
  'for_use_0ad_public-gui-campaigns_vi.po'
  'for_use_0ad_public-gui-gamesetup_vi.po'
  'for_use_0ad_public-gui-ingame_vi.po'
  'for_use_0ad_public-gui-lobby_vi.po'
  'for_use_0ad_public-gui-manual_vi.po'
  'for_use_0ad_public-gui-other_vi.po'
  'for_use_0ad_public-gui-userreport_vi.po'
  'for_use_0ad_public-maps_vi.po'
  'for_use_0ad_public-simulation-auras_vi.po'
  'for_use_0ad_public-simulation-other_vi.po'
  'for_use_0ad_public-simulation-technologies_vi.po'
  'for_use_0ad_public-templates-buildings_vi.po'
  'for_use_0ad_public-templates-other_vi.po'
  'for_use_0ad_public-templates-units_vi.po'
  'for_use_0ad_public-tutorials_vi.po'
)
sha1sums=(
  'SKIP' # LICENSE
  'SKIP' # mod.json
  'SKIP' # for_use_0ad_engine_vi.po
  'SKIP' # for_use_0ad_mod-selector_vi.po
  'SKIP' # for_use_0ad_public-civilizations_vi.po
  'SKIP' # for_use_0ad_public-gui-campaigns_vi.po
  'SKIP' # for_use_0ad_public-gui-gamesetup_vi.po
  'SKIP' # for_use_0ad_public-gui-ingame_vi.po
  'SKIP' # for_use_0ad_public-gui-lobby_vi.po
  'SKIP' # for_use_0ad_public-gui-manual_vi.po
  'SKIP' # for_use_0ad_public-gui-other_vi.po
  'SKIP' # for_use_0ad_public-gui-userreport_vi.po
  'SKIP' # for_use_0ad_public-maps_vi.po
  'SKIP' # for_use_0ad_public-simulation-auras_vi.po
  'SKIP' # for_use_0ad_public-simulation-other_vi.po
  'SKIP' # for_use_0ad_public-simulation-technologies_vi.po
  'SKIP' # for_use_0ad_public-templates-buildings_vi.po
  'SKIP' # for_use_0ad_public-templates-other_vi.po
  'SKIP' # for_use_0ad_public-templates-units_vi.po
  'SKIP' # for_use_0ad_public-tutorials_vi.po
)

_verify_modjson_field() {
  local field=$1
  local expected=$2
  local received=$(jq --raw-output ".$field" 'mod.json')
  echo "    checking mod.json#$field: $expected == $received"
  [[ "$received" == $expected ]]
}

_run() {
  echo "    > $*"
  $@
}

build() {
  msg2 'Validating mod.json...'
  _verify_modjson_field 'name' 'vi-lang'
  _verify_modjson_field 'version' "$pkgver"
  _verify_modjson_field 'url' "$url"
  _verify_modjson_field 'dependencies[]' "0ad=0.0.$_0ad_patch"

  msg2 'Creating directory tree...'
  _run mkdir -p l10n
  for src in for_use_*_vi.po; do
    renamed=$(echo "$src" | sed 's/for_use_0ad_/vi./' | sed 's/_vi\.po/.po/')
    dest=l10n/$renamed
    _run cp "$src" "$dest"
  done
}

package() {
  _run install -d "$pkgdir/usr/share/0ad/data/mods/vi-lang"
  _run cp -r 'l10n' "$pkgdir/usr/share/0ad/data/mods/vi-lang/l10n"
  _run install -Dm644 'mod.json' "$pkgdir/usr/share/0ad/data/mods/vi-lang/mod.json"
  _run install -Dm644 'LICENSE' "$pkgdir/usr/share/licenses/0ad-vi-lang/LICENSE"
}
