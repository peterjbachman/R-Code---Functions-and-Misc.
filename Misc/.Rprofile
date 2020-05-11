if (interactive()) {
  rsthemes::set_theme_light("Xcode")
  rsthemes::set_theme_dark("Kiss")
}

if (interactive() && requireNamespace("rsthemes", quietly = TRUE)) {
  # Set preferred themes if not handled elsewhere..
  rsthemes::set_theme_light("Xcode")  # light theme
  rsthemes::set_theme_dark("Kiss") # dark theme
  
  # Whenever the R session restarts inside RStudio...
  setHook("rstudio.sessionInit", function(isNewSession) {
    # Automatically choose the correct theme based on time of day
    day <- suncalc::getSunlightTimes(
      date = Sys.Date(), 
      lat = 41.7, 
      lon = -111.8, 
      keep = c("sunrise", "sunset"), 
      tz = Sys.timezone()
    )
    sunrise <- day$sunrise
    sunrise <- as.data.frame(strsplit(as.character(sunrise),' '))[2,]
    sunset <- day$sunset
    sunset <- as.data.frame(strsplit(as.character(sunset),' '))[2,]
    rsthemes::use_theme_auto(dark_start = sunset, dark_end = sunrise)
  }, action = "append")
}
