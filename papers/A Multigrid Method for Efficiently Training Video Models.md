# A Multigrid Method for Efficiently Training Video Models

The [paper](https://arxiv.org/abs/1912.00998) has been accepted by CVPR2020 (oral) (I have not found it on the CVPR official website but on the [Kaiming He page](http://kaiminghe.com/) though.)

## Personal Feeling

After skimming and scanning reading and intensive reading (like two times) the main idea behind the paper is simple : to use a cycling changeable mini-batch size to speed up the training. A main concern of me is whether the method could become a standard like data augmentation in image model and decaying learning schedule in almost every optimizer would do. If so, I admit it will be "accessible, scalable, and economical" like the paper said and maybe become a part of future video framework like [transforms](https://pytorch.org/docs/stable/torchvision/transforms.html) in pytorch (But like some papers I have read before, I don't think it is a very sophisticated work to explore some deep aspects, but no offense only my personal feeling:)

## Quotations and Graffiti

> However what is the optimal shape? High resolution models perform well but train slowly. Low resolution models train fast but they are inaccurate.

We often have to make a choice to keep something balanced, like save lives or incomes during the pandemic. Model input shape is a hyperparameter which is fixed and always decided by one certain model like 224 for ResNet34. So in order to ingratiate that we have to change our original shape and resolution. Is that rational or optimal? Seems not. The value of the questions the authors raise, I think, is that even some common settings are necessary to question.

-----------------

> Inspired by multigrid methods in numerical optimization, we propose to use variable mini-batch shapes with different spatial-temporal resolutions that are varied according to a schedule.
>
> ...we can draw a connection to **multigrid methods** in numerical analysis.
>
> [He and Xu](https://link.springer.com/content/pdf/10.1007/s11425-019-9547-2.pdf) connect multigrid methods to deep networks through identifying the correspondence between steps in traditional multigrid methods and operators in a convolutional neural network.
>
> Inspired by multigrid methods in numerical analysis, which solve optimization problems on alternating coarse and fine grids, the core observation in this paper is that the underlying sampling grid that is used to train video models need not to be constant during training.

What is more interesting to me when I reading a paper is what exactly inspires the author to do the research. I mean the first hit in his/her mind. I know it is an accumulated process but the most inspiring previous work or observations always exists, right? (Like [Enlightenment in Buddhism](https://simple.wikipedia.org/wiki/Enlightenment_(Buddhism)) ([顿悟]([https://zh.wikipedia.org/wiki/%E9%A0%93%E6%82%9F](https://zh.wikipedia.org/wiki/頓悟)))? not very appropriate though...)  Now here it is! The multigrid method is borrowed from [the same method in numerical analysis](https://en.wikipedia.org/wiki/Multigrid_method). In fact a lot of terms like sampling grid and long/short cycle filled with the whole paper are just from there (The first time I met the gird sampling method is in the class of *Bayesian Analysis*). Some teachers always complain graduate students pay much attention to their everyday class (always in the first year) and not their project or work. That seems reasonable because many courses (Like many math courses) are not that related to the project and they say when you use something in the project just search it and study it then. Well I don't very agree. Some fundamental lessons need to learn it systematically and theoretically. Not everything must be useful NOW. And the idea behind the lessons is always profound, transferable and heuristic! This paper is another justification. The [analogy](https://en.wikipedia.org/wiki/Analogy) happens only you have learnt and understood it. 

-------------

> The central idea of this paper is to avoid this trade-off i.e. to have faster training without losing accuracy -- by making the mini-batch shape variable during training.

I like this sentence especially "avoid this trade-off". We always say how to get a balance and how to make a trade-off. But here the different attitude is how to avoid the trade-off or win all. Ambitious, right? But the author achieves that actually.

--------------

> [He et al.](https://arxiv.org/pdf/1406.4729.pdf) change the input shapes but fix the mini-batch size. These methods show that training with variable scales can be beneficial.

For the image, the proposed SPPnet model in [He et al.](https://arxiv.org/pdf/1406.4729.pdf) has already used the changing input shape. I will check this paper later. Multi-scale is another inspiration to the author. I think in many cases we use the thoughts of multi-scale. I will summarize it later and update it when I think of something later.

-------

> Each video in a dataset is a discrete signal that was sampled from an underlying continuous signal generated by the physical world....When using one of these source videos in a training mini-batch, a sampling grid is used to resample it.

I like this sentence too. It recognizes a signal - video from a brand new prospective as sampling from the real world. That is it! After reading the sentence, I raised up my head, have a look at the atmosphere, and yes, I have already sampled a clip of video! Amazing, right? Then it builds a connection to the sampling process and naturally the sampling grid.  

## Fancy terms

* out-of-the-box
* schedule
* weight sharing
* sampling grid
* akin to
* coarse and fine
* multi-scale
* underlying

This is a beautiful word I have met, meaning "real but not immediately obvious". It shows a paradox that is a contradiction of surface and innate. Like, "On the surface it is a very funny novel but it does have a more serious underlying theme." "It is important to look at all the underlying causes of the conflict." That makes think of the [Iceberg theory](https://en.wikipedia.org/wiki/Iceberg_theory) of Hemingway. I can't stop post some quotes:

> Hemingway said that only the tip of the iceberg showed in fiction—your reader will see only what is above the water—but the knowledge that you have about your character that never makes it into the story acts as the bulk of the iceberg. And that is what gives your story weight and gravitas.

Almost every paper uses the word as far as I know.

## Explore more

* multi-scale

  This is a key idea in the area, which is related to the hierarchy. I will list some areas I met this before (need to update):

  1.  object detecting. (Seems yolo?)
  2. 