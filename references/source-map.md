# Vela Browser source map

This reference applies only when the project is Vela Browser or follows the same Android/Compose structure. Confirm the paths before using them.

## Visual entry points

- `app/src/main/java/com/velaweb/browser/theme/Color.kt`: semantic palette.
- `app/src/main/java/com/velaweb/browser/theme/Theme.kt`: Material color scheme.
- `app/src/main/java/com/velaweb/browser/theme/Type.kt`: existing font system. Preserve it unless the design changes typography.
- `app/src/main/res/values/colors.xml`: Android resource colors.
- `app/src/main/res/values/themes.xml`: window and splash colors, plus system-bar appearance.
- `app/src/main/java/com/velaweb/browser/utils/SystemBarsColorEffect.kt`: runtime status and navigation icon appearance.

## Shared UI

- `ui/components/SearchBar.kt`: home and search entry presentation.
- `ui/components/TabBar.kt`: main navigation selection treatment.
- `ui/components/AppButton.kt`: shared button colors and shape.
- `ui/components/AppToolbar.kt`: top bar surface and back action.

## High-traffic screens

- `ui/home/HomeScreen.kt`: hero, search placement, actions, and section headings.
- `ui/home/components/HomeFeatureShortcuts.kt`: clean, weather, bookmarks, and history entry tiles.
- `ui/home/components/QuickLinksSection.kt`: quick-access grid and add action.
- `ui/home/components/NewsCard.kt`: news hierarchy and card surface.
- `ui/main/MainScreen.kt`: main tab container.
- `ui/files/FileScreen.kt`, `ui/tabs/TabScreen.kt`, `ui/more/MoreScreen.kt`: secondary visual systems.

## Behavior that must stay put

- `Navigation.kt` and `NavigationKeys.kt`: routes and transitions.
- `browser/tab/`: tab limits, incognito behavior, and WebView lifecycle.
- `ui/home/HomeScreenViewModel.kt` and other ViewModels: state and data flow.
- Module boundaries under `data_*`, `core_*`, and `utils`: data access and infrastructure.

Check `values-night` resources before assuming the app always follows the main palette. Do not delete a night variant unless the user explicitly wants one permanent appearance and the source behavior has been checked.
