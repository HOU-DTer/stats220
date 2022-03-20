1. The meme is to combine nine images together, six are online pictures and three are created black blocks with annotations, they are stacked with three on each other. These combined images are to show three types of dogs and the three actions they would like to do. One dog likes one action.
2. For the new meme we put the original meme in code fence as a chunk of code with commonts for each steps to explain what is doing.
3. The combined image is shown at the bottom.

```r

# load the magick library
library(magick)

# read the images from websites, they are three types of dogs and three types of things they would like to do.
border_collie <- image_read("https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg9.chongwu.cc%2Fd%2Ffile%2Fbianmu%2F201310%2F575f08c38b70112377e367a689330b89.jpg&refer=http%3A%2F%2Fimg9.chongwu.cc&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1649661126&t=6dbf69f1851e03cb2e00b9883d1fc35d") %>% image_scale(500)
dog_food <- image_read("https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.xiaokeai.com%2Fuploadfile%2F2020%2F0921%2F20200921034257842.jpg&refer=http%3A%2F%2Fimg.xiaokeai.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1650339472&t=2be30ccce23db8d58fec269075e706a5") %>% image_resize("500x500") %>% image_blur(10,5)

husky <- image_read("https://gimg2.baidu.com/image_search/src=http%3A%2F%2Feuro-premium.cn%2Fsites%2Fdefault%2Ffiles%2F2017%2F06%2F2017-06-13-020.jpg&refer=http%3A%2F%2Feuro-premium.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1649660953&t=8f62cdd991fac0a04bde4383b0e4d061") %>% image_scale(500)
dog_swimming <- image_read("https://img2.baidu.com/it/u=531342792,3502212661&fm=253&fmt=auto&app=138&f=JPEG?w=452&h=300") %>% image_resize("500x500") %>% image_flip()

samoye <- image_read("https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fwww.quchong.cn%2Fuploads%2F210531%2F106-210531135635D3.jpg&refer=http%3A%2F%2Fwww.quchong.cn&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1649660942&t=6dd404ce9bad23cf212823b30299c1e7") %>% image_scale(500)
dog_tools <- image_read("https://img2.baidu.com/it/u=3861410943,3348131614&fm=253&fmt=auto&app=138&f=JPEG?w=652&h=500") %>% image_resize("500x500") %>% image_flop()

# black square one with annotation
border_collie_text <- image_blank(width = 500, height = 500,color = "#000000") %>% 
  image_annotate(text="border\ncollie\nlikes\neating", color = "#FFFFFF", size = 80, font = "Impact", gravity="center")

# black square two with annotation
husky_text <- image_blank(width = 500, height = 500,color = "#000000") %>% 
  image_annotate(text="husky\nlikes\nswimming", color = "#FFFFFF", size = 80, font = "Impact", gravity="center")

# black square three with annotation
samoye_text <- image_blank(width = 500, height = 500,color = "#000000") %>% 
  image_annotate(text="samoye\nlikes\nplaying", color = "#FFFFFF", size = 80, font = "Impact", gravity="center")

# construct first row
first_row <- c(border_collie, border_collie_text, dog_food) %>% image_append()
  
# construct second row  
second_row <- c(husky, husky_text, dog_swimming) %>% image_append()

# construct third row  
third_row <- c(samoye, samoye_text, dog_tools) %>% image_append()

# combind the three rows together
c(first_row, second_row, third_row) %>% image_append(stack = TRUE)

# stack the three rows and assign to a variable called meme
meme <- c(first_row, second_row, third_row) %>% image_append(stack = TRUE)

# save and store meme as a png file called my_meme.png
image_write(meme,"my_meme.png")

```
![my_meme.png](https://github.com/HOU-DTer/stats220/blob/main/my_meme.png)
![my_meme](https://user-images.githubusercontent.com/70314010/159152675-e46ed72a-04ba-4d67-be68-6a57e8de9d72.png)
