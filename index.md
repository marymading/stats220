library(magick)

spongebob_happy <- image_read("https://i.imgflip.com/697gxz.jpg") %>% image_scale(300)

spongebob_sad<- image_read("https://i.imgflip.com/5l3pc.jpg") %>% image_scale(300)
#Top Meme
kdrama_text <- image_blank(width = 560, height = 385, 
                           color = "#f2f2f2") %>% 
               image_annotate(text = "Watching 16 episodes k-drama",
                           color = "#000000", size = 40, 
                           font = "sans-serif", gravity = "center")

happy_vector <- c(spongebob_happy, kdrama_text) %>%
                image_append()
#Bottom Meme
lecture_text <- image_blank(width = 560, height = 222, 
                               color = "#f2f2f2") %>% 
                image_annotate(text = "Watching 1 hour lecture",
                               color = "#000000", size = 40, 
                               font = "sans-serif", gravity = "center")
sad_vector <- c(spongebob_sad, lecture_text) %>%image_append()


#Completed Meme
meme <- c(happy_vector, sad_vector) %>%
  image_append(stack = TRUE)

#save as image
image_write(meme, "my_meme.png")
