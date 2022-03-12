```r

library(magick)

border_collie <- image_read("https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg9.chongwu.cc%2Fd%2Ffile%2Fbianmu%2F201310%2F575f08c38b70112377e367a689330b89.jpg&refer=http%3A%2F%2Fimg9.chongwu.cc&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1649661126&t=6dbf69f1851e03cb2e00b9883d1fc35d") %>% image_scale(500)

husky <- image_read("https://gimg2.baidu.com/image_search/src=http%3A%2F%2Feuro-premium.cn%2Fsites%2Fdefault%2Ffiles%2F2017%2F06%2F2017-06-13-020.jpg&refer=http%3A%2F%2Feuro-premium.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1649660953&t=8f62cdd991fac0a04bde4383b0e4d061") %>% image_scale(500)

samoye <- image_read("https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fwww.quchong.cn%2Fuploads%2F210531%2F106-210531135635D3.jpg&refer=http%3A%2F%2Fwww.quchong.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1649660942&t=6dd404ce9bad23cf212823b30299c1e7") %>% image_scale(500)

border_collie_text <- image_blank(width = 500, height = 500,color = "#000000") %>% 
  image_annotate(text="border\ncollie", color = "#FFFFFF", size = 80, font = "Impact", gravity="center")

husky_text <- image_blank(width = 500, height = 500,color = "#000000") %>% 
  image_annotate(text="husky", color = "#FFFFFF", size = 80, font = "Impact", gravity="center")

samoye_text <- image_blank(width = 500, height = 500,color = "#000000") %>% 
  image_annotate(text="samoye", color = "#FFFFFF", size = 80, font = "Impact", gravity="center")

first_row <- c(border_collie, border_collie_text) %>% image_append()
  
second_row <- c(husky, husky_text) %>% image_append()
  
third_row <- c(samoye, samoye_text) %>% image_append()

meme <- c(first_row, second_row, third_row) %>% image_append(stack = TRUE)

image_write(meme,"my_meme.png")
```
