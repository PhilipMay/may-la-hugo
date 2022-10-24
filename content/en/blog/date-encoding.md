---
title: Options for Date Encoding
date: 2022-10-12
tags:
  - encoding
  - date
  - time
categories:
  - Data
---

Some data, such as strings, must be encoded to be used in machine learning models. Here we explore the different options for encoding date fields.

{{< figure src="/img/posts/calendar.jpg" caption="Photo by [Behnam Norouzi](https://unsplash.com/@behy_studio?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/)" >}}

The general options to encode the time dimension like the birth date of a customer or the production time of a product are:

1. separate encoding of year, month and maybe also day and weekday
2. relative to a certain point in time in the past - e.g. number of days after January 1st 1900
3. relative to "today" - e.g. number of days before today

## Pros and cons: separate encoding of year, month and maybe also day and weekday
If you believe in astrology this might be your favorite to encode a birth date since the month is preserved. If you want to encode a *production date* it also might be useful to encode the weekday. That is because there might be a relation between product quality in production and weekday. Parts manufactured on Mondays may have the most severe quality variations.

The disadvantage is that you need multiple columns to encode the date.
Furthermore, this approach also suffers from a
[concept drift](https://en.wikipedia.org/wiki/Concept_drift) problem (see below).

## Pros and cons: relative to a certain point in time in the past
This is easy to calculate because the "point in time in the past" (January 1st 1900 for example) is a fixed point in time. This contrasts with the encoding which is relative to "today". But the problem with this encoding is the following:

There are circumstances that in reality are not related to the date itself, but much more to the age. The remaining service life of a technical device is much more directly related to its age than to its production date. Whether a customer is interested in an airplane trip or a train ticket also depends on age and not so much on the date of birth. So, if you represent the date of birth relative to a time in the past, then the resulting model would have a built-in [concept drift](https://en.wikipedia.org/wiki/Concept_drift).

For example, two predictions are made for the same person with his or her date of birth. One prediction on January 2022 and one on January 2023. Then the person is obviously one year older at the second prediction in January 2023. But this would not be visible in the encoding of the date of birth (if you encode it relative to a point in time in the past). The model would therefore experience a concept drift and would have to be re-trained.

## Pros and cons: relative to "today"
This would be the encoding of choice if there is a relation between age and prediction. It would prevent the concept drift described above. The disadvantage of the coding is that the reference day "today" is very dynamic and not fixed. So you have to be very careful how you set "today".

A distinction is made between the generation of the training data (validation- and testdata) and the prediction at production time. The prediction at production time is easy to understand. The "today" is just the day where the prediction is made. However, generating the training data is a bit more difficult. "Today" must not be the day on which the training data was generated. Instead, the day "today" is relative to the day on which the label was "created". The easiest way to explain this is to use an example:

We assume that we have parts (for example hard disks) that were produced on a certain date. Now we want to predict when the hard disks have another week to live. For this we have the times at which a hard disk fails. Let's take a very simplified example:

The hard disk was manufactured on January 1, 2022. It has already failed on January 25, 2022. We want to create a training data set that represents day 7 before the failure. The "today" in this case is January 18, 2022, so the production date of the hard disk, which we represent relative to "today", is encoded with a 17. This is exactly the age (in days) of the hard disk on the day "today".

## Conclusion

If your prediction is correlated with the age of something, choose the encoding we call "relative to today". This removes the concept drift but is a bit tricky to calculate. If  there is an actual relation to the birth or production date, month or the day of the week then encode this information as described above.
