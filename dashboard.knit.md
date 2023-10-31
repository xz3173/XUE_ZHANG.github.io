---
title: "Dashboard"
output: 
  flexdashboard::flex_dashboard:
    orientation: columns
    vertical_layout: fill
---





```r
library(tidyverse)
```

```
## ── Attaching core tidyverse packages ─────────── tidyverse 2.0.0 ──
## ✔ dplyr     1.1.3     ✔ readr     2.1.4
## ✔ forcats   1.0.0     ✔ stringr   1.5.0
## ✔ ggplot2   3.4.3     ✔ tibble    3.2.1
## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
## ✔ purrr     1.0.2     
## ── Conflicts ───────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
```

```r
library(p8105.datasets)

library(plotly)
```

```
## 
## Attaching package: 'plotly'
## 
## The following object is masked from 'package:ggplot2':
## 
##     last_plot
## 
## The following object is masked from 'package:stats':
## 
##     filter
## 
## The following object is masked from 'package:graphics':
## 
##     layout
```


```r
data("instacart")
```

Column {data-width=650}
-----------------------------------------------------------------------

### Chart A


```r
# Summarizing the data by aisle_id
summary_data = instacart |>
  group_by(aisle_id, aisle) |>
  summarize(
    total_orders = n(),
    avg_reordered_rate = mean(reordered, na.rm = TRUE)
  ) |>
  arrange(-total_orders) 
```

```
## `summarise()` has grouped output by 'aisle_id'. You can override
## using the `.groups` argument.
```

```r
# Plotting the data
summary_data |>
  plot_ly(x = ~aisle,
          y = ~avg_reordered_rate,
          text = ~aisle,
          type = "scatter",
          mode = "markers") |>
  layout(title = "Relationship between Aisle Popularity and Reorder Rate",
         xaxis = list(title = "Aisles (Ordered by Popularity)"),
         yaxis = list(title = "Average Reorder Rate"))
```

```{=html}
<div class="plotly html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-e4ec6aacea12df3942cf" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-e4ec6aacea12df3942cf">{"x":{"visdat":{"6353117bfc2":["function () ","plotlyVisDat"]},"cur_data":"6353117bfc2","attrs":{"6353117bfc2":{"x":{},"y":{},"text":{},"mode":"markers","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Relationship between Aisle Popularity and Reorder Rate","xaxis":{"domain":[0,1],"automargin":true,"title":"Aisles (Ordered by Popularity)","type":"category","categoryorder":"array","categoryarray":["air fresheners candles","asian foods","baby accessories","baby bath body care","baby food formula","bakery desserts","baking ingredients","baking supplies decor","beauty","beers coolers","body lotions soap","bread","breakfast bakery","breakfast bars pastries","bulk dried fruits vegetables","bulk grains rice dried goods","buns rolls","butter","candy chocolate","canned fruit applesauce","canned jarred vegetables","canned meals beans","canned meat seafood","cat food care","cereal","chips pretzels","cleaning products","cocoa drink mixes","coffee","cold flu allergy","condiments","cookies cakes","crackers","cream","deodorants","diapers wipes","digestion","dish detergents","dog food care","doughs gelatins bake mixes","dry pasta","eggs","energy granola bars","energy sports drinks","eye ear care","facial care","feminine care","first aid","food storage","fresh dips tapenades","fresh fruits","fresh herbs","fresh pasta","fresh vegetables","frozen appetizers sides","frozen breads doughs","frozen breakfast","frozen dessert","frozen juice","frozen meals","frozen meat seafood","frozen pizza","frozen produce","frozen vegan vegetarian","fruit vegetable snacks","grains rice dried goods","granola","hair care","honeys syrups nectars","hot cereal pancake mixes","hot dogs bacon sausage","ice cream ice","ice cream toppings","indian foods","instant foods","juice nectars","kitchen supplies","kosher foods","latino foods","laundry","lunch meat","marinades meat preparation","meat counter","milk","mint gum","missing","more household","muscles joints pain relief","nuts seeds dried fruit","oils vinegars","oral hygiene","other","other creams cheeses","packaged cheese","packaged meat","packaged poultry","packaged produce","packaged seafood","packaged vegetables fruits","paper goods","pasta sauce","pickled goods olives","plates bowls cups flatware","popcorn jerky","poultry counter","prepared meals","prepared soups salads","preserved dips spreads","protein meal replacements","red wines","refrigerated","refrigerated pudding desserts","salad dressing toppings","seafood counter","shave needs","skin care","soap","soft drinks","soup broth bouillon","soy lactosefree","specialty cheeses","specialty wines champagnes","spices seasonings","spirits","spreads","tea","tofu meat alternatives","tortillas flat bread","trail mix snack mix","trash bags liners","vitamins supplements","water seltzer sparkling water","white wines","yogurt"]},"yaxis":{"domain":[0,1],"automargin":true,"title":"Average Reorder Rate"},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":["fresh vegetables","fresh fruits","packaged vegetables fruits","yogurt","packaged cheese","water seltzer sparkling water","milk","chips pretzels","soy lactosefree","bread","refrigerated","ice cream ice","frozen produce","eggs","crackers","frozen meals","energy granola bars","lunch meat","soft drinks","cereal","fresh herbs","fresh dips tapenades","soup broth bouillon","juice nectars","packaged produce","baby food formula","baking ingredients","other creams cheeses","hot dogs bacon sausage","paper goods","canned jarred vegetables","nuts seeds dried fruit","cream","spreads","canned meals beans","candy chocolate","dry pasta","oils vinegars","butter","cookies cakes","instant foods","breakfast bakery","condiments","pasta sauce","frozen breakfast","tea","spices seasonings","frozen appetizers sides","coffee","tortillas flat bread","missing","frozen pizza","asian foods","popcorn jerky","fruit vegetable snacks","hot cereal pancake mixes","grains rice dried goods","cleaning products","packaged poultry","poultry counter","preserved dips spreads","tofu meat alternatives","buns rolls","pickled goods olives","doughs gelatins bake mixes","energy sports drinks","frozen vegan vegetarian","salad dressing toppings","laundry","prepared meals","canned fruit applesauce","specialty cheeses","dish detergents","granola","latino foods","frozen meat seafood","canned meat seafood","meat counter","breakfast bars pastries","oral hygiene","prepared soups salads","food storage","marinades meat preparation","cat food care","honeys syrups nectars","soap","body lotions soap","vitamins supplements","plates bowls cups flatware","beers coolers","other","refrigerated pudding desserts","fresh pasta","trash bags liners","dog food care","protein meal replacements","frozen breads doughs","packaged meat","bakery desserts","hair care","trail mix snack mix","cold flu allergy","red wines","digestion","diapers wipes","baking supplies decor","white wines","seafood counter","air fresheners candles","cocoa drink mixes","feminine care","spirits","mint gum","frozen dessert","packaged seafood","muscles joints pain relief","more household","deodorants","facial care","bulk dried fruits vegetables","indian foods","bulk grains rice dried goods","kosher foods","eye ear care","first aid","skin care","shave needs","ice cream toppings","specialty wines champagnes","kitchen supplies","baby bath body care","baby accessories","frozen juice","beauty"],"y":[0.60665697269087504,0.73622510350694148,0.65640248174996496,0.68680304127443881,0.59706467781001937,0.73766283420269274,0.79230486459992644,0.59640538552560041,0.68772865853658538,0.68005077215993226,0.65567418632684693,0.47600987828541191,0.56041508929764394,0.72895597484276731,0.58697427521437318,0.60150375939849621,0.59768468107054851,0.60800849206817242,0.64960992689968666,0.58737114992901673,0.53301769249937703,0.61695945053493595,0.44549606194983121,0.60034843205574917,0.7174591381872214,0.55265949386270652,0.31448655256723718,0.58447737909516384,0.57558729415437448,0.54844808570978421,0.45468885558798011,0.523938716884775,0.68873421819359015,0.49529003470500743,0.54323084763037199,0.56491748886754567,0.48504160028323595,0.37052730696798492,0.60226950354609932,0.56442885771543083,0.5042855702329333,0.65333468683382401,0.3400390023606692,0.50965488907148726,0.65011820330969272,0.52773037542662116,0.16531953874339908,0.54768883878241259,0.6133222116301239,0.56027774452292589,0.38152951157435461,0.59979114998042027,0.35464535464535463,0.59548937400607205,0.60213618157543392,0.50566750629722923,0.41718291490055431,0.3171021377672209,0.63355920114122677,0.63671274961597546,0.4892058596761758,0.65235213741948073,0.54313415116739217,0.46743138058172878,0.41698192517864652,0.64656263180092788,0.59339961920880047,0.35621953803771983,0.46117342536669542,0.63368013549479796,0.56206206206206211,0.49883810999225409,0.40878552971576226,0.58664212463844334,0.42249154453213078,0.55492367554624367,0.50725084850354829,0.5530231085786641,0.60591603053435117,0.36286644951140062,0.59741144414168934,0.26359256710254647,0.29604130808950085,0.65233968804159448,0.37325418994413406,0.34871979805265058,0.35002339728591486,0.32757745048247844,0.40377743746809597,0.60957041870581841,0.38830083565459611,0.5575477154424523,0.54238329238329241,0.36150524367674275,0.59057071960297769,0.49689826302729528,0.54242819843342038,0.53604193971166447,0.50499666888740835,0.26684819605173588,0.63636363636363635,0.21842496285289748,0.58648431214802899,0.44232365145228214,0.47700631199278631,0.17550274223034734,0.68382352941176472,0.55627306273062727,0.34208059981255856,0.44067796610169491,0.33396946564885494,0.58738366080661841,0.61954261954261958,0.4598698481561822,0.54455445544554459,0.34894091415830547,0.25925925925925924,0.27272727272727271,0.34450402144772119,0.6055172413793104,0.4422809457579972,0.54731861198738174,0.3503184713375796,0.27372262773722628,0.21706864564007422,0.25842696629213485,0.2857142857142857,0.29761904761904762,0.50976138828633411,0.18303571428571427,0.26829268292682928,0.565359477124183,0.47278911564625853,0.22996515679442509],"text":["fresh vegetables","fresh fruits","packaged vegetables fruits","yogurt","packaged cheese","water seltzer sparkling water","milk","chips pretzels","soy lactosefree","bread","refrigerated","ice cream ice","frozen produce","eggs","crackers","frozen meals","energy granola bars","lunch meat","soft drinks","cereal","fresh herbs","fresh dips tapenades","soup broth bouillon","juice nectars","packaged produce","baby food formula","baking ingredients","other creams cheeses","hot dogs bacon sausage","paper goods","canned jarred vegetables","nuts seeds dried fruit","cream","spreads","canned meals beans","candy chocolate","dry pasta","oils vinegars","butter","cookies cakes","instant foods","breakfast bakery","condiments","pasta sauce","frozen breakfast","tea","spices seasonings","frozen appetizers sides","coffee","tortillas flat bread","missing","frozen pizza","asian foods","popcorn jerky","fruit vegetable snacks","hot cereal pancake mixes","grains rice dried goods","cleaning products","packaged poultry","poultry counter","preserved dips spreads","tofu meat alternatives","buns rolls","pickled goods olives","doughs gelatins bake mixes","energy sports drinks","frozen vegan vegetarian","salad dressing toppings","laundry","prepared meals","canned fruit applesauce","specialty cheeses","dish detergents","granola","latino foods","frozen meat seafood","canned meat seafood","meat counter","breakfast bars pastries","oral hygiene","prepared soups salads","food storage","marinades meat preparation","cat food care","honeys syrups nectars","soap","body lotions soap","vitamins supplements","plates bowls cups flatware","beers coolers","other","refrigerated pudding desserts","fresh pasta","trash bags liners","dog food care","protein meal replacements","frozen breads doughs","packaged meat","bakery desserts","hair care","trail mix snack mix","cold flu allergy","red wines","digestion","diapers wipes","baking supplies decor","white wines","seafood counter","air fresheners candles","cocoa drink mixes","feminine care","spirits","mint gum","frozen dessert","packaged seafood","muscles joints pain relief","more household","deodorants","facial care","bulk dried fruits vegetables","indian foods","bulk grains rice dried goods","kosher foods","eye ear care","first aid","skin care","shave needs","ice cream toppings","specialty wines champagnes","kitchen supplies","baby bath body care","baby accessories","frozen juice","beauty"],"mode":"markers","type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.20000000000000001,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```

Column {data-width=350}
-----------------------------------------------------------------------

### Chart B


```r
# Define a threshold for popular products, for example, the top 30
top_n_products = 30

# Extract the most popular products
popular_products = instacart |>
  count(product_id, product_name) |>
  arrange(-n) |>
  slice_head(n = top_n_products) |>
  pull(product_name)

# Filter the main data for only popular products
filtered_data = instacart |>
  filter(product_name %in% popular_products)

# Plotting the data using plotly
plot_ly(data = filtered_data,
        x = ~order_hour_of_day,
        y = ~product_name, 
        type = "box",
        colors = "viridis") |>
  
  layout(title = "Distribution of Purchase Hours for Popular Products",
         xaxis = list(title = "Hour of Day"),
         yaxis = list(title = "Product"))
```

```{=html}
<div class="plotly html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-7101c78a8d1c7d00414a" style="width:672px;height:480px;"></div>
```

### Chart C


```r
# filtering aisles with more than 10000 items ordered
instacart |>
  group_by(aisle) |>
  summarise(order_count = n()) |>
  filter(order_count > 10000) |>
  arrange(order_count) |>

# plotting
  plot_ly(
    x = ~aisle,
    y = ~order_count,
    type = "bar",
    colors = "viridis") |>
  layout(title = "Nubmer of Items Ordered in Each Aisle",
         xaxis = list(title = "Aisle"),
         yaxis = list(title = "Nuber of Items Ordered"))
```

```{=html}
<div class="plotly html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-e004d6f532c07863e1f6" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-e004d6f532c07863e1f6">{"x":{"visdat":{"6354990c0f7":["function () ","plotlyVisDat"]},"cur_data":"6354990c0f7","attrs":{"6354990c0f7":{"x":{},"y":{},"colors":"viridis","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Nubmer of Items Ordered in Each Aisle","xaxis":{"domain":[0,1],"automargin":true,"title":"Aisle","type":"category","categoryorder":"array","categoryarray":["baby food formula","baking ingredients","bread","butter","candy chocolate","canned jarred vegetables","canned meals beans","cereal","chips pretzels","crackers","cream","dry pasta","eggs","energy granola bars","fresh dips tapenades","fresh fruits","fresh herbs","fresh vegetables","frozen meals","frozen produce","hot dogs bacon sausage","ice cream ice","juice nectars","lunch meat","milk","nuts seeds dried fruit","oils vinegars","other creams cheeses","packaged cheese","packaged produce","packaged vegetables fruits","paper goods","refrigerated","soft drinks","soup broth bouillon","soy lactosefree","spreads","water seltzer sparkling water","yogurt"]},"yaxis":{"domain":[0,1],"automargin":true,"title":"Nuber of Items Ordered"},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":["butter","oils vinegars","dry pasta","candy chocolate","canned meals beans","spreads","cream","nuts seeds dried fruit","canned jarred vegetables","paper goods","hot dogs bacon sausage","other creams cheeses","baking ingredients","baby food formula","packaged produce","juice nectars","soup broth bouillon","fresh dips tapenades","fresh herbs","cereal","soft drinks","lunch meat","energy granola bars","frozen meals","crackers","eggs","frozen produce","ice cream ice","refrigerated","bread","soy lactosefree","chips pretzels","milk","water seltzer sparkling water","packaged cheese","yogurt","packaged vegetables fruits","fresh fruits","fresh vegetables"],"y":[10575,10620,11298,11453,11774,12102,12356,12532,12679,12694,12813,12820,13088,13198,13460,14350,15109,15142,16052,16201,16279,16957,17449,18221,19592,19875,22453,22676,23228,23635,26240,31269,32644,36617,41699,55240,78493,150473,150609],"type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.20000000000000001,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
```
