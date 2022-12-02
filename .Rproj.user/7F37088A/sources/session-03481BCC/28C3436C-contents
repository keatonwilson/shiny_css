# CSS Shiny Demo
# Keaton Wilson
# keaton@virgalabs.io
# 2022-12-01


# Packages ----------------------------------------------------------------
library(shiny)
library(shinydashboard)


# UI ----------------------------------------------------------------------

ui <- fluidPage(
    ### HTML Header
    tags$head(
      tags$style(HTML("
                      @import url('https://fonts.googleapis.com/css2?family=Rubik+Microbe&display=swap');
                      h1 {
                        font-family: 'Rubik Microbe';
                      }")
                 )
    ),
    ### Separate CSS Sheet
    includeCSS("www/styles.css"),
    # Application title
    titlePanel("Old Faithful Geyser Data"),

    # Sidebar with a slider input for number of bins
    sidebarLayout(
        sidebarPanel(
            ### STYLE ARGUMENT WITHIN ELEMENTS
            h1("This is title text that can be styled",
               style = "font-weight: 800; color: #4d3a7d;"),
            sliderInput("bins",
                        "Number of bins:",
                        min = 1,
                        max = 50,
                        value = 30)
        ),

        # Show a plot of the generated distribution
        mainPanel(
          p("this is normal body text"),
          box(class = "plotting_box",
              plotOutput("distPlot"),
          )
        )
    )
)

# Define server logic required to draw a histogram
server <- function(input, output) {

    output$distPlot <- renderPlot({
        # generate bins based on input$bins from ui.R
        x    <- faithful[, 2]
        bins <- seq(min(x), max(x), length.out = input$bins + 1)

        # draw the histogram with the specified number of bins
        hist(x, breaks = bins, col = 'darkgray', border = 'white',
             xlab = 'Waiting time to next eruption (in mins)',
             main = 'Histogram of waiting times')
    })
}

# Run the application
shinyApp(ui = ui, server = server)
