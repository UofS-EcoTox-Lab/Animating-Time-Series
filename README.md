### Animating time-series

[gganimate](https://github.com/thomasp85/gganimate/wiki) is a great package for creating animated plots for presentations, the web, etc.

Here I'll make a pretty simple plot of active layer depths through time.

```
library(gganimate)

rm(list = ls())
```

#### 1. Read in the data

`
hare <- read.csv(file = "~/Desktop/Workspace/Earthwatch/thaw.hf.csv", header = TRUE)
`

#### 2. Basic line plot using ggplot

```````
p <- ggplot(data = hare, aes(x = year, y = mean))+
  geom_line(color = "pink", size = 1) + 
  scale_y_reverse(name = "Thaw depth (cm)", limits = c(80,40)) + 
  scale_x_continuous(name ="Year", limits=c(1990,2020)) +
  theme_bw() + 
  theme(axis.text.x = element_text(size = 12),
        axis.text.y = element_text(size = 12)) 
```````

<img src="https://user-images.githubusercontent.com/44586553/69080251-3776d080-0a01-11ea-9fc2-564cb226b66e.jpg" width="500" height="400">

#### 3. Animate the plot

`
p + transition_reveal(year)
`

![Hare](https://user-images.githubusercontent.com/44586553/69080607-eddab580-0a01-11ea-9d35-f71221e779f8.gif)
