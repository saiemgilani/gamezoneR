
<!-- README.md is generated from README.Rmd. Please edit that file -->

# 

# gamezoneR <a href='http://jacklich10.github.io/gamezoneR'><img src="https://raw.githubusercontent.com/JackLich10/gamezoneR/master/man/figures/gamezoneR_40trans.png" align="right" width="20%" min-width="100px"/></a>

<!-- badges: start -->
<!-- badges: end -->

`gamezoneR` is an R package for working with NCAA Men’s Basketball
play-by-play data from STATS LLC’s
[GameZone](http://gamezone.stats.com/). The package allows users to
scrape team and master schedules as well as play-by-play data with shot
locations into a tidy format. The main benefit of `gamezoneR` is the
volume of shot location data available. While ESPN also charts shots, as
of March 10th 2021, ESPN has charted approximately 70,000 shots while
STATS LLC has charted over 170,000 from the 2020-21 college basketball
season alone!

## Installation

You can install `gamezoneR` from
[GitHub](https://github.com/JackLich10/gamezoneR) with:

``` r
# Install via devtools package using the following:
devtools::install_github(repo = "JackLich10/gamezoneR")
```

## Getting started

For a quick introduction to the package, visit the Intro to `gamezoneR`
[article](https://jacklich10.github.io/gamezoneR/articles/intro-to-gamezoneR.html).

If you want to load in all available play-by-play data dating back to
the 2017-18 season, use the following code:

``` r
future::plan("multisession")
tictoc::tic()
progressr::with_progress({
  pbp <- gamezoneR::load_gamezone_pbp(gamezoneR:::available_seasons())
})
tictoc::toc()
## 48.078 sec elapsed
length(unique(pbp$game_id))
## 24,994 games
pbp %>% dplyr::filter(!is.na(loc_x)) %>% nrow()
## 2,843,392 shot locations
```

## Documentation

For more information on the package and function reference, please see
the `gamezoneR`
[documentation](https://jacklich10.github.io/gamezoneR/index.html).

## Code of Conduct

Please note that the `gamezoneR` project is released with a [Contributor
Code of
Conduct](https://contributor-covenant.org/version/2/0/CODE_OF_CONDUCT.html).
By contributing to this project, you agree to abide by its terms.
