suppressPackageStartupMessages(library(here))
suppressPackageStartupMessages(library(tidyverse))
list.files(here("data"))
reds <- read_delim(here("Data", "winequality-red.csv"),
                   delim=";",
                   show_col_types = FALSE)
suppressPackageStartupMessages(library(corrplot))
suppressPackageStartupMessages(library(pls))
suppressPackageStartupMessages(library(glmnet))
suppressPackageStartupMessages(library(e1071))
suppressPackageStartupMessages(library(ROCR))
suppressPackageStartupMessages(library(brant))
suppressPackageStartupMessages(library(VGAM))
suppressPackageStartupMessages(library(nnet))


## Wine Quality
names(reds) = c("fixed_acidity", "volatile_acidity", "citric_acid",
                "residual_sugar" ,"chlorides", "free_sulfur_dioxide",
          "total_sulfur_dioxide", "density", "pH",
          "sulphates", "alcohol", "quality")
#reds %>%
 # mutate(quality_numeric = quality,
  #       quality_factor = factor(quality)) %>%
  #select(-quality)-> reds

reds %>%
  mutate(quality= factor(quality)) -> reds

## Heart Data

heart_data <-read_delim("https://archive.ics.uci.edu/ml/machine-learning-databases/heart-disease/processed.cleveland.data",
                        show_col_types = FALSE,
                         col_names = F)
heart_data = as.tibble(heart_data)
names(heart_data) = 
  c("Age",
    "Sex",
    "CP",
    "trestbps",
    "chol",
    "fbs",
    "restecg",
    "thalach",
    "exang",
    "oldpeak",
    "slope",
    "ca",
    "thal",
    "Number")


# Another consideration: flattening the response variable to a binary (0 = no heart disease,
# 1 = heart disease) setting

heart_data %>%
  mutate(Number = recode(Number,
                         `2` = 1,
                         `3` = 1,
                         `4` = 1)) -> heart_data

# A third consideration
heart_data %>%
  mutate(Sex = factor(Sex),
         CP = factor(CP),
         restecg = factor(restecg),
         exang = factor(exang),
         slope = factor(slope),
         thal = factor(thal)) ->heart_data
