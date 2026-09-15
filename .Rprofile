set_up <- function() {
  if (!requireNamespace("pak", quietly = TRUE)) install.packages("pak")
  if (!requireNamespace("renv", quietly = TRUE)) pak::pak("renv")
  
  remotes <- c(
    "stan-dev/cmdstanr",
    "stefanocoretta/coretta2018itaegg"
  )
  
  # Install GitHub packages
  pak::pak(remotes)
  
  # Get list of necessary packages
  deps <- unique(renv::dependencies()[,2])
  
  # Drop GitHub packages from deps list. pak doesn't know where to find them.
  deps <- setdiff(
    deps,
    c("cmdstanr", "coretta2018itaegg")
  )
  
  # Install all dependencies (except the ones from GitHub)
  pak::pak(c(deps))
  
  cmdstanr::check_cmdstan_toolchain()
}
