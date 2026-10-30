# The Puppet Master Writeup

> Category : OSINT

> Trainee,
> 
> Our investigation into the cryptocurrency funding trail has led us to RivalTech Corporation. A recent data breach at their corporate servers has exposed internal communications, employee records, and strategic planning documents.
> 
> Your mission is to navigate the BreachScope database and identify the senior executive who orchestrated the comprehensive fake review campaign against XyloPhone Inc. Look for evidence of direct approval, budget authorization, and campaign coordination.
> 
> Submit your findings in the format: HTB{executive_identification}. Example: HTB{CEO_Thomas_Wilson_Approved_Budget}
> 
> – Training Division Digital Forensics Unit

## Solution

Upon visiting the link http://154.57.164.66:32115 to view the challenge, we found an image of an armored military vehicle in the "Evidence Analysis" section.
The "Investigation Challenge" section also includes a few questions about this vehicle that we need to answer.

To answer the first question you can easily search on the web like `Google lens`.

> What type of military vehicle is shown in the image? Look at the vehicle's characteristics: it's wheeled, armored, and appears to be a personnel carrier. Research similar vehicles online.
> 
> Bushmaster

Now to answer all the next questions you can use https://en.wikipedia.org/wiki/Bushmaster_Protected_Mobility_Vehicle.

> Who is the manufacturer/designer of this vehicle? Research the company that designed and produces this specific armored vehicle.
> 
> Thales Australia

> When did this vehicle first enter military service? Research the year this specific vehicle type was first deployed operationally.
> 
> 1997

> What is the country of origin for this vehicle? Research where this specific vehicle was originally designed and manufactured.
> 
> Australia

> What is the passenger capacity of this vehicle? Research how many passengers plus crew it can carry (format: X passengers and Y driver).
> 
> 9 passengers and 1 driver

After answering all the questions we can have the flag.

```text
HTB{c0mb1n1ng_r34l_w0rld_4nd_s3lf_c0nt41n3d_OSINT!}
```

