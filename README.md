# Generating-Keywords-for-Googles-Ad
Generating-Keywords-for-Googles-Ad
1. The brief
Imagine working for a digital marketing agency, and the agency is approached by a massive online retailer of furniture. They want to test our skills at creating large campaigns for all of their website. We are tasked with creating a prototype set of keywords for search campaigns for their sofas section. The client says that they want us to generate keywords for the following products:

sofas
convertible sofas
love seats
recliners
sofa beds
The brief: The client is generally a low-cost retailer, offering many promotions and discounts. We will need to focus on such keywords. We will also need to move away from luxury keywords and topics, as we are targeting price-sensitive customers. Because we are going to be tight on budget, it would be good to focus on a tightly targeted set of keywords and make sure they are all set to exact and phrase match.

Based on the brief above we will first need to generate a list of words, that together with the products given above would make for good keywords. Here are some examples:

Products: sofas, recliners
Words: buy, prices
The resulting keywords: 'buy sofas', 'sofas buy', 'buy recliners', 'recliners buy', 'prices sofas', 'sofas prices', 'prices recliners', 'recliners prices'.

As a final result, we want to have a DataFrame that looks like this:

Campaign	Ad Group	Keyword	Criterion Type
Campaign1	AdGroup_1	keyword 1a	Exact
Campaign1	AdGroup_1	keyword 1a	Phrase
Campaign1	AdGroup_1	keyword 1b	Exact
Campaign1	AdGroup_1	keyword 1b	Phrase
Campaign1	AdGroup_2	keyword 2a	Exact
Campaign1	AdGroup_2	keyword 2a	Phrase
The first step is to come up with a list of words that users might use to express their desire in buying low-cost sofas.

# List of words to pair with products
words = ['buy', 'price', 'sale', 'discount', 'promo', 'shop', 'promotion', 'outlet', 'cheap', 'for sale']

# Print list of words
print(words)
['buy', 'price', 'sale', 'discount', 'promo', 'shop', 'promotion', 'outlet', 'cheap', 'for sale']
2. Combine the words with the product names
Imagining all the possible combinations of keywords can be stressful! But not for us, because we are keyword ninjas! We know how to translate campaign briefs into Python data structures and can imagine the resulting DataFrames that we need to create.

Now that we have brainstormed the words that work well with the brief that we received, it is now time to combine them with the product names to generate meaningful search keywords. We want to combine every word with every product once before, and once after, as seen in the example above.

As a quick reminder, for the product 'recliners' and the words 'buy' and 'price' for example, we would want to generate the following combinations:

buy recliners
recliners buy
price recliners
recliners price
…

and so on for all the words and products that we have.

products = ['sofas', 'convertible sofas', 'love seats', 'recliners', 'sofa beds']

# Create an empty list
keywords_list = []

# Loop through products
for product in products :
    # Loop through words
    for word in words:
        # Append combinations
        keywords_list.append([product, product + ' ' + word])
        keywords_list.append([word, word + ' ' + product])
        
# Inspect keyword list
from pprint import pprint
pprint(keywords_list)
[['sofas', 'sofas buy'],
 ['buy', 'buy sofas'],
 ['sofas', 'sofas price'],
 ['price', 'price sofas'],
 ['sofas', 'sofas sale'],
 ['sale', 'sale sofas'],
 ['sofas', 'sofas discount'],
 ['discount', 'discount sofas'],
 ['sofas', 'sofas promo'],
 ['promo', 'promo sofas'],
 ['sofas', 'sofas shop'],
 ['shop', 'shop sofas'],
 ['sofas', 'sofas promotion'],
 ['promotion', 'promotion sofas'],
 ['sofas', 'sofas outlet'],
 ['outlet', 'outlet sofas'],
 ['sofas', 'sofas cheap'],
 ['cheap', 'cheap sofas'],
 ['sofas', 'sofas for sale'],
 ['for sale', 'for sale sofas'],
 ['convertible sofas', 'convertible sofas buy'],
 ['buy', 'buy convertible sofas'],
 ['convertible sofas', 'convertible sofas price'],
 ['price', 'price convertible sofas'],
 ['convertible sofas', 'convertible sofas sale'],
 ['sale', 'sale convertible sofas'],
 ['convertible sofas', 'convertible sofas discount'],
 ['discount', 'discount convertible sofas'],
 ['convertible sofas', 'convertible sofas promo'],
 ['promo', 'promo convertible sofas'],
 ['convertible sofas', 'convertible sofas shop'],
 ['shop', 'shop convertible sofas'],
 ['convertible sofas', 'convertible sofas promotion'],
 ['promotion', 'promotion convertible sofas'],
 ['convertible sofas', 'convertible sofas outlet'],
 ['outlet', 'outlet convertible sofas'],
 ['convertible sofas', 'convertible sofas cheap'],
 ['cheap', 'cheap convertible sofas'],
 ['convertible sofas', 'convertible sofas for sale'],
 ['for sale', 'for sale convertible sofas'],
 ['love seats', 'love seats buy'],
 ['buy', 'buy love seats'],
 ['love seats', 'love seats price'],
 ['price', 'price love seats'],
 ['love seats', 'love seats sale'],
 ['sale', 'sale love seats'],
 ['love seats', 'love seats discount'],
 ['discount', 'discount love seats'],
 ['love seats', 'love seats promo'],
 ['promo', 'promo love seats'],
 ['love seats', 'love seats shop'],
 ['shop', 'shop love seats'],
 ['love seats', 'love seats promotion'],
 ['promotion', 'promotion love seats'],
 ['love seats', 'love seats outlet'],
 ['outlet', 'outlet love seats'],
 ['love seats', 'love seats cheap'],
 ['cheap', 'cheap love seats'],
 ['love seats', 'love seats for sale'],
 ['for sale', 'for sale love seats'],
 ['recliners', 'recliners buy'],
 ['buy', 'buy recliners'],
 ['recliners', 'recliners price'],
 ['price', 'price recliners'],
 ['recliners', 'recliners sale'],
 ['sale', 'sale recliners'],
 ['recliners', 'recliners discount'],
 ['discount', 'discount recliners'],
 ['recliners', 'recliners promo'],
 ['promo', 'promo recliners'],
 ['recliners', 'recliners shop'],
 ['shop', 'shop recliners'],
 ['recliners', 'recliners promotion'],
 ['promotion', 'promotion recliners'],
 ['recliners', 'recliners outlet'],
 ['outlet', 'outlet recliners'],
 ['recliners', 'recliners cheap'],
 ['cheap', 'cheap recliners'],
 ['recliners', 'recliners for sale'],
 ['for sale', 'for sale recliners'],
 ['sofa beds', 'sofa beds buy'],
 ['buy', 'buy sofa beds'],
 ['sofa beds', 'sofa beds price'],
 ['price', 'price sofa beds'],
 ['sofa beds', 'sofa beds sale'],
 ['sale', 'sale sofa beds'],
 ['sofa beds', 'sofa beds discount'],
 ['discount', 'discount sofa beds'],
 ['sofa beds', 'sofa beds promo'],
 ['promo', 'promo sofa beds'],
 ['sofa beds', 'sofa beds shop'],
 ['shop', 'shop sofa beds'],
 ['sofa beds', 'sofa beds promotion'],
 ['promotion', 'promotion sofa beds'],
 ['sofa beds', 'sofa beds outlet'],
 ['outlet', 'outlet sofa beds'],
 ['sofa beds', 'sofa beds cheap'],
 ['cheap', 'cheap sofa beds'],
 ['sofa beds', 'sofa beds for sale'],
 ['for sale', 'for sale sofa beds']]
3. Convert the list of lists into a DataFrame
Now we want to convert this list of lists into a DataFrame so we can easily manipulate it and manage the final output.

# Load library
import pandas as pd

# Create a DataFrame from list
keywords_df = pd.DataFrame.from_records(keywords_list)

# Print the keywords DataFrame to explore it
keywords_df
0	1
0	sofas	sofas buy
1	buy	buy sofas
2	sofas	sofas price
3	price	price sofas
4	sofas	sofas sale
5	sale	sale sofas
6	sofas	sofas discount
7	discount	discount sofas
8	sofas	sofas promo
9	promo	promo sofas
10	sofas	sofas shop
11	shop	shop sofas
12	sofas	sofas promotion
13	promotion	promotion sofas
14	sofas	sofas outlet
15	outlet	outlet sofas
16	sofas	sofas cheap
17	cheap	cheap sofas
18	sofas	sofas for sale
19	for sale	for sale sofas
20	convertible sofas	convertible sofas buy
21	buy	buy convertible sofas
22	convertible sofas	convertible sofas price
23	price	price convertible sofas
24	convertible sofas	convertible sofas sale
25	sale	sale convertible sofas
26	convertible sofas	convertible sofas discount
27	discount	discount convertible sofas
28	convertible sofas	convertible sofas promo
29	promo	promo convertible sofas
...	...	...
70	recliners	recliners shop
71	shop	shop recliners
72	recliners	recliners promotion
73	promotion	promotion recliners
74	recliners	recliners outlet
75	outlet	outlet recliners
76	recliners	recliners cheap
77	cheap	cheap recliners
78	recliners	recliners for sale
79	for sale	for sale recliners
80	sofa beds	sofa beds buy
81	buy	buy sofa beds
82	sofa beds	sofa beds price
83	price	price sofa beds
84	sofa beds	sofa beds sale
85	sale	sale sofa beds
86	sofa beds	sofa beds discount
87	discount	discount sofa beds
88	sofa beds	sofa beds promo
89	promo	promo sofa beds
90	sofa beds	sofa beds shop
91	shop	shop sofa beds
92	sofa beds	sofa beds promotion
93	promotion	promotion sofa beds
94	sofa beds	sofa beds outlet
95	outlet	outlet sofa beds
96	sofa beds	sofa beds cheap
97	cheap	cheap sofa beds
98	sofa beds	sofa beds for sale
99	for sale	for sale sofa beds
100 rows × 2 columns

4. Rename the columns of the DataFrame
Before we can upload this table of keywords, we will need to give the columns meaningful names. If we inspect the DataFrame we just created above, we can see that the columns are currently named 0 and 1. Ad Group (example: "sofas") and Keyword (example: "sofas buy") are much more appropriate names.

# Rename the columns of the DataFrame
keywords_df = keywords_df.rename(columns={0: 'Ad Group', 1: 'Keyword'})
keywords_df
Ad Group	Keyword
0	sofas	sofas buy
1	buy	buy sofas
2	sofas	sofas price
3	price	price sofas
4	sofas	sofas sale
5	sale	sale sofas
6	sofas	sofas discount
7	discount	discount sofas
8	sofas	sofas promo
9	promo	promo sofas
10	sofas	sofas shop
11	shop	shop sofas
12	sofas	sofas promotion
13	promotion	promotion sofas
14	sofas	sofas outlet
15	outlet	outlet sofas
16	sofas	sofas cheap
17	cheap	cheap sofas
18	sofas	sofas for sale
19	for sale	for sale sofas
20	convertible sofas	convertible sofas buy
21	buy	buy convertible sofas
22	convertible sofas	convertible sofas price
23	price	price convertible sofas
24	convertible sofas	convertible sofas sale
25	sale	sale convertible sofas
26	convertible sofas	convertible sofas discount
27	discount	discount convertible sofas
28	convertible sofas	convertible sofas promo
29	promo	promo convertible sofas
...	...	...
70	recliners	recliners shop
71	shop	shop recliners
72	recliners	recliners promotion
73	promotion	promotion recliners
74	recliners	recliners outlet
75	outlet	outlet recliners
76	recliners	recliners cheap
77	cheap	cheap recliners
78	recliners	recliners for sale
79	for sale	for sale recliners
80	sofa beds	sofa beds buy
81	buy	buy sofa beds
82	sofa beds	sofa beds price
83	price	price sofa beds
84	sofa beds	sofa beds sale
85	sale	sale sofa beds
86	sofa beds	sofa beds discount
87	discount	discount sofa beds
88	sofa beds	sofa beds promo
89	promo	promo sofa beds
90	sofa beds	sofa beds shop
91	shop	shop sofa beds
92	sofa beds	sofa beds promotion
93	promotion	promotion sofa beds
94	sofa beds	sofa beds outlet
95	outlet	outlet sofa beds
96	sofa beds	sofa beds cheap
97	cheap	cheap sofa beds
98	sofa beds	sofa beds for sale
99	for sale	for sale sofa beds
100 rows × 2 columns

5. Add a campaign column
Now we need to add some additional information to our DataFrame. We need a new column called Campaign for the campaign name. We want campaign names to be descriptive of our group of keywords and products, so let's call this campaign 'SEM_Sofas'.

# Add a campaign column
keywords_df['Campaign'] = 'SEM_Sofas'
keywords_df
Ad Group	Keyword	Campaign
0	sofas	sofas buy	SEM_Sofas
1	buy	buy sofas	SEM_Sofas
2	sofas	sofas price	SEM_Sofas
3	price	price sofas	SEM_Sofas
4	sofas	sofas sale	SEM_Sofas
5	sale	sale sofas	SEM_Sofas
6	sofas	sofas discount	SEM_Sofas
7	discount	discount sofas	SEM_Sofas
8	sofas	sofas promo	SEM_Sofas
9	promo	promo sofas	SEM_Sofas
10	sofas	sofas shop	SEM_Sofas
11	shop	shop sofas	SEM_Sofas
12	sofas	sofas promotion	SEM_Sofas
13	promotion	promotion sofas	SEM_Sofas
14	sofas	sofas outlet	SEM_Sofas
15	outlet	outlet sofas	SEM_Sofas
16	sofas	sofas cheap	SEM_Sofas
17	cheap	cheap sofas	SEM_Sofas
18	sofas	sofas for sale	SEM_Sofas
19	for sale	for sale sofas	SEM_Sofas
20	convertible sofas	convertible sofas buy	SEM_Sofas
21	buy	buy convertible sofas	SEM_Sofas
22	convertible sofas	convertible sofas price	SEM_Sofas
23	price	price convertible sofas	SEM_Sofas
24	convertible sofas	convertible sofas sale	SEM_Sofas
25	sale	sale convertible sofas	SEM_Sofas
26	convertible sofas	convertible sofas discount	SEM_Sofas
27	discount	discount convertible sofas	SEM_Sofas
28	convertible sofas	convertible sofas promo	SEM_Sofas
29	promo	promo convertible sofas	SEM_Sofas
...	...	...	...
70	recliners	recliners shop	SEM_Sofas
71	shop	shop recliners	SEM_Sofas
72	recliners	recliners promotion	SEM_Sofas
73	promotion	promotion recliners	SEM_Sofas
74	recliners	recliners outlet	SEM_Sofas
75	outlet	outlet recliners	SEM_Sofas
76	recliners	recliners cheap	SEM_Sofas
77	cheap	cheap recliners	SEM_Sofas
78	recliners	recliners for sale	SEM_Sofas
79	for sale	for sale recliners	SEM_Sofas
80	sofa beds	sofa beds buy	SEM_Sofas
81	buy	buy sofa beds	SEM_Sofas
82	sofa beds	sofa beds price	SEM_Sofas
83	price	price sofa beds	SEM_Sofas
84	sofa beds	sofa beds sale	SEM_Sofas
85	sale	sale sofa beds	SEM_Sofas
86	sofa beds	sofa beds discount	SEM_Sofas
87	discount	discount sofa beds	SEM_Sofas
88	sofa beds	sofa beds promo	SEM_Sofas
89	promo	promo sofa beds	SEM_Sofas
90	sofa beds	sofa beds shop	SEM_Sofas
91	shop	shop sofa beds	SEM_Sofas
92	sofa beds	sofa beds promotion	SEM_Sofas
93	promotion	promotion sofa beds	SEM_Sofas
94	sofa beds	sofa beds outlet	SEM_Sofas
95	outlet	outlet sofa beds	SEM_Sofas
96	sofa beds	sofa beds cheap	SEM_Sofas
97	cheap	cheap sofa beds	SEM_Sofas
98	sofa beds	sofa beds for sale	SEM_Sofas
99	for sale	for sale sofa beds	SEM_Sofas
100 rows × 3 columns

6. Create the match type column
There are different keyword match types. One is exact match, which is for matching the exact term or are close variations of that exact term. Another match type is broad match, which means ads may show on searches that include misspellings, synonyms, related searches, and other relevant variations.

Straight from Google's AdWords documentation:

In general, the broader the match type, the more traffic potential that keyword will have, since your ads may be triggered more often. Conversely, a narrower match type means that your ads may show less often—but when they do, they’re likely to be more related to someone’s search.

Since the client is tight on budget, we want to make sure all the keywords are in exact match at the beginning.

# Add a criterion type column
keywords_df['Criterion Type'] = 'Exact'
keywords_df
Ad Group	Keyword	Campaign	Criterion Type
0	sofas	sofas buy	SEM_Sofas	Exact
1	buy	buy sofas	SEM_Sofas	Exact
2	sofas	sofas price	SEM_Sofas	Exact
3	price	price sofas	SEM_Sofas	Exact
4	sofas	sofas sale	SEM_Sofas	Exact
5	sale	sale sofas	SEM_Sofas	Exact
6	sofas	sofas discount	SEM_Sofas	Exact
7	discount	discount sofas	SEM_Sofas	Exact
8	sofas	sofas promo	SEM_Sofas	Exact
9	promo	promo sofas	SEM_Sofas	Exact
10	sofas	sofas shop	SEM_Sofas	Exact
11	shop	shop sofas	SEM_Sofas	Exact
12	sofas	sofas promotion	SEM_Sofas	Exact
13	promotion	promotion sofas	SEM_Sofas	Exact
14	sofas	sofas outlet	SEM_Sofas	Exact
15	outlet	outlet sofas	SEM_Sofas	Exact
16	sofas	sofas cheap	SEM_Sofas	Exact
17	cheap	cheap sofas	SEM_Sofas	Exact
18	sofas	sofas for sale	SEM_Sofas	Exact
19	for sale	for sale sofas	SEM_Sofas	Exact
20	convertible sofas	convertible sofas buy	SEM_Sofas	Exact
21	buy	buy convertible sofas	SEM_Sofas	Exact
22	convertible sofas	convertible sofas price	SEM_Sofas	Exact
23	price	price convertible sofas	SEM_Sofas	Exact
24	convertible sofas	convertible sofas sale	SEM_Sofas	Exact
25	sale	sale convertible sofas	SEM_Sofas	Exact
26	convertible sofas	convertible sofas discount	SEM_Sofas	Exact
27	discount	discount convertible sofas	SEM_Sofas	Exact
28	convertible sofas	convertible sofas promo	SEM_Sofas	Exact
29	promo	promo convertible sofas	SEM_Sofas	Exact
...	...	...	...	...
70	recliners	recliners shop	SEM_Sofas	Exact
71	shop	shop recliners	SEM_Sofas	Exact
72	recliners	recliners promotion	SEM_Sofas	Exact
73	promotion	promotion recliners	SEM_Sofas	Exact
74	recliners	recliners outlet	SEM_Sofas	Exact
75	outlet	outlet recliners	SEM_Sofas	Exact
76	recliners	recliners cheap	SEM_Sofas	Exact
77	cheap	cheap recliners	SEM_Sofas	Exact
78	recliners	recliners for sale	SEM_Sofas	Exact
79	for sale	for sale recliners	SEM_Sofas	Exact
80	sofa beds	sofa beds buy	SEM_Sofas	Exact
81	buy	buy sofa beds	SEM_Sofas	Exact
82	sofa beds	sofa beds price	SEM_Sofas	Exact
83	price	price sofa beds	SEM_Sofas	Exact
84	sofa beds	sofa beds sale	SEM_Sofas	Exact
85	sale	sale sofa beds	SEM_Sofas	Exact
86	sofa beds	sofa beds discount	SEM_Sofas	Exact
87	discount	discount sofa beds	SEM_Sofas	Exact
88	sofa beds	sofa beds promo	SEM_Sofas	Exact
89	promo	promo sofa beds	SEM_Sofas	Exact
90	sofa beds	sofa beds shop	SEM_Sofas	Exact
91	shop	shop sofa beds	SEM_Sofas	Exact
92	sofa beds	sofa beds promotion	SEM_Sofas	Exact
93	promotion	promotion sofa beds	SEM_Sofas	Exact
94	sofa beds	sofa beds outlet	SEM_Sofas	Exact
95	outlet	outlet sofa beds	SEM_Sofas	Exact
96	sofa beds	sofa beds cheap	SEM_Sofas	Exact
97	cheap	cheap sofa beds	SEM_Sofas	Exact
98	sofa beds	sofa beds for sale	SEM_Sofas	Exact
99	for sale	for sale sofa beds	SEM_Sofas	Exact
100 rows × 4 columns

7. Duplicate all the keywords into 'phrase' match
The great thing about exact match is that it is very specific, and we can control the process very well. The tradeoff, however, is that:

The search volume for exact match is lower than other match types
We can't possibly think of all the ways in which people search, and so, we are probably missing out on some high-quality keywords.
So it's good to use another match called phrase match as a discovery mechanism to allow our ads to be triggered by keywords that include our exact match keywords, together with anything before (or after) them.

Later on, when we launch the campaign, we can explore with modified broad match, broad match, and negative match types, for better visibility and control of our campaigns.

# Making a copy of the keywords DataFrame
keywords_phrase = keywords_df.copy()

# Changing criterion type match to phrase
keywords_phrase['Criterion Type']= 'Phrase'
# Appending the DataFrames
keywords_df_final = keywords_df.append(keywords_phrase)
keywords_df_final
Ad Group	Keyword	Campaign	Criterion Type
0	sofas	sofas buy	SEM_Sofas	Exact
1	buy	buy sofas	SEM_Sofas	Exact
2	sofas	sofas price	SEM_Sofas	Exact
3	price	price sofas	SEM_Sofas	Exact
4	sofas	sofas sale	SEM_Sofas	Exact
5	sale	sale sofas	SEM_Sofas	Exact
6	sofas	sofas discount	SEM_Sofas	Exact
7	discount	discount sofas	SEM_Sofas	Exact
8	sofas	sofas promo	SEM_Sofas	Exact
9	promo	promo sofas	SEM_Sofas	Exact
10	sofas	sofas shop	SEM_Sofas	Exact
11	shop	shop sofas	SEM_Sofas	Exact
12	sofas	sofas promotion	SEM_Sofas	Exact
13	promotion	promotion sofas	SEM_Sofas	Exact
14	sofas	sofas outlet	SEM_Sofas	Exact
15	outlet	outlet sofas	SEM_Sofas	Exact
16	sofas	sofas cheap	SEM_Sofas	Exact
17	cheap	cheap sofas	SEM_Sofas	Exact
18	sofas	sofas for sale	SEM_Sofas	Exact
19	for sale	for sale sofas	SEM_Sofas	Exact
20	convertible sofas	convertible sofas buy	SEM_Sofas	Exact
21	buy	buy convertible sofas	SEM_Sofas	Exact
22	convertible sofas	convertible sofas price	SEM_Sofas	Exact
23	price	price convertible sofas	SEM_Sofas	Exact
24	convertible sofas	convertible sofas sale	SEM_Sofas	Exact
25	sale	sale convertible sofas	SEM_Sofas	Exact
26	convertible sofas	convertible sofas discount	SEM_Sofas	Exact
27	discount	discount convertible sofas	SEM_Sofas	Exact
28	convertible sofas	convertible sofas promo	SEM_Sofas	Exact
29	promo	promo convertible sofas	SEM_Sofas	Exact
...	...	...	...	...
70	recliners	recliners shop	SEM_Sofas	Phrase
71	shop	shop recliners	SEM_Sofas	Phrase
72	recliners	recliners promotion	SEM_Sofas	Phrase
73	promotion	promotion recliners	SEM_Sofas	Phrase
74	recliners	recliners outlet	SEM_Sofas	Phrase
75	outlet	outlet recliners	SEM_Sofas	Phrase
76	recliners	recliners cheap	SEM_Sofas	Phrase
77	cheap	cheap recliners	SEM_Sofas	Phrase
78	recliners	recliners for sale	SEM_Sofas	Phrase
79	for sale	for sale recliners	SEM_Sofas	Phrase
80	sofa beds	sofa beds buy	SEM_Sofas	Phrase
81	buy	buy sofa beds	SEM_Sofas	Phrase
82	sofa beds	sofa beds price	SEM_Sofas	Phrase
83	price	price sofa beds	SEM_Sofas	Phrase
84	sofa beds	sofa beds sale	SEM_Sofas	Phrase
85	sale	sale sofa beds	SEM_Sofas	Phrase
86	sofa beds	sofa beds discount	SEM_Sofas	Phrase
87	discount	discount sofa beds	SEM_Sofas	Phrase
88	sofa beds	sofa beds promo	SEM_Sofas	Phrase
89	promo	promo sofa beds	SEM_Sofas	Phrase
90	sofa beds	sofa beds shop	SEM_Sofas	Phrase
91	shop	shop sofa beds	SEM_Sofas	Phrase
92	sofa beds	sofa beds promotion	SEM_Sofas	Phrase
93	promotion	promotion sofa beds	SEM_Sofas	Phrase
94	sofa beds	sofa beds outlet	SEM_Sofas	Phrase
95	outlet	outlet sofa beds	SEM_Sofas	Phrase
96	sofa beds	sofa beds cheap	SEM_Sofas	Phrase
97	cheap	cheap sofa beds	SEM_Sofas	Phrase
98	sofa beds	sofa beds for sale	SEM_Sofas	Phrase
99	for sale	for sale sofa beds	SEM_Sofas	Phrase
200 rows × 4 columns

8. Save and summarize!
To upload our campaign, we need to save it as a CSV file. Then we will be able to import it to AdWords editor or BingAds editor. There is also the option of pasting the data into the editor if we want, but having easy access to the saved data is great so let's save to a CSV file!

Looking at a summary of our campaign structure is good now that we've wrapped up our keyword work. We can do that by grouping by ad group and criterion type and counting by keyword. This summary shows us that we assigned specific keywords to specific ad groups, which are each part of a campaign. In essence, we are telling Google (or Bing, etc.) that we want any of the words in each ad group to trigger one of the ads in the same ad group. Separately, we will have to create another table for ads, which is a task for another day and would look something like this:

Campaign	Ad Group	Headline 1	Headline 2	Description	Final URL
SEM_Sofas	Sofas	Looking for Quality Sofas?	Explore Our Massive Collection	30-day Returns With Free Delivery Within the US. Start Shopping Now	DataCampSofas.com/sofas
SEM_Sofas	Sofas	Looking for Affordable Sofas?	Check Out Our Weekly Offers	30-day Returns With Free Delivery Within the US. Start Shopping Now	DataCampSofas.com/sofas
SEM_Sofas	Recliners	Looking for Quality Recliners?	Explore Our Massive Collection	30-day Returns With Free Delivery Within the US. Start Shopping Now	DataCampSofas.com/recliners
SEM_Sofas	Recliners	Need Affordable Recliners?	Check Out Our Weekly Offers	30-day Returns With Free Delivery Within the US. Start Shopping Now	DataCampSofas.com/recliners
Together, these tables get us the sample keywords -> ads -> landing pages mapping shown in the diagram below.

Keywords-Ads-Landing pages flow

# Saving the final keywords to a CSV file
keywords_df_final.to_csv('keywords.csv', index=False)

# Viewing a summary of our campaign work
summary = keywords_df_final.groupby(['Ad Group', 'Criterion Type'])['Keyword'].count()
print(summary)
Ad Group           Criterion Type
buy                Exact              5
                   Phrase             5
cheap              Exact              5
                   Phrase             5
convertible sofas  Exact             10
                   Phrase            10
discount           Exact              5
                   Phrase             5
for sale           Exact              5
                   Phrase             5
love seats         Exact             10
                   Phrase            10
outlet             Exact              5
                   Phrase             5
price              Exact              5
                   Phrase             5
promo              Exact              5
                   Phrase             5
promotion          Exact              5
                   Phrase             5
recliners          Exact             10
                   Phrase            10
sale               Exact              5
                   Phrase             5
shop               Exact              5
                   Phrase             5
sofa beds          Exact             10
                   Phrase            10
sofas              Exact             10
                   Phrase            10
Name: Keyword, dtype: int64
