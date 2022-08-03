# Computing-or-creating-new-variables-
#COMPUTING OR CREATING NEW VARIABLES ###
### Loading the libraries ###
pacman::p_load(pacman, rio, tidyverse)

### loading and preparing the dataset (Google search data) 
data<- import("StateData.xlsx") %>% as_tibble() %>% select(state_code, 
          psychRegions, instagram:modernDance) %>% 
        mutate(psychRegions = as.factor(psychRegions))

view(data) # viewing the data 

### Creating new variables as a result of the averages of old variables 

newdata<- data %>% mutate(Philant = (entrepreneur + gdpr + museum + university) / 3,
                          Patrick = (volunteering + museum + scrapbook + modernDance) / 4) %>% 
               select(state_code,psychRegions, Philant, Patrick)
view(newdata)


### Doing a reverse coding 

newdata2 <- data %>%  mutate(Houseowner = (university + (mortgage * -1)) / 2 )%>% 
           select(state_code, Houseowner, university, mortgage)
view(newdata2)  

### There are two package that is more convenient in working with reverse codeing 
# install.packages("psych")
# install.packages("scales")  
  
