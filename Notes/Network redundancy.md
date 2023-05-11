2305100853
	Status: #Exam #CCNA
		Tags: [[CCNA 200-301]] [[Networking]]

# Network redundancy

<img src = 'https://i.gyazo.com/339a4e3df7d34938af1260292bc52a10.png'>



The first line creates a static route from R1 to the SP (internet) with a AD of 1

The second line creates a backup route to R2 by setting the AD to 5 because a static route AD (1)

The third line focuses on south direction traffic if link G0/1 goes down it sends traffic to R2 
- A directly connected route has an AD of 0 hence why this static route doesn't need to have its AD changed.



















---
# Reference