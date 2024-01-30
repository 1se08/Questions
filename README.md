# Questions

#I'm building a code to calculate odds ratio using logistic regression in r software
#I'm wondering how to calculate the standard error of the odds ratio using the coefficients i get from logistic regression

des <- svydesign(ids=~1, data=d, weights=d$FinalWgt)
model <- svyglm(formula = smoker ~ sec_family + sec_public + sec_school, subset(des, age %in% c(13, 14, 15) & !is.na(d$smoker)), family = binomial)

summary_model <- summary(model)
odds_ratio <- as.data.frame(exp(summary_model$coef[,1]))
se <- as.data.frame(exp(summary_model$coef[,1]) * summary_model$coef[,2])
