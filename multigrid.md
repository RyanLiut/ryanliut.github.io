# A Multigrid Method for Efficiently Training Video Models

The [paper](https://arxiv.org/abs/1912.00998) has been accepted by CVPR2020 (oral) (I have not found it on the CVPR official website but on the [Kaiming He page](http://kaiminghe.com/) though.)

## Personal Feeling

After skimming and scanning reading and intensive reading (like two times) the main idea behind the paper is simple : to use a cycling changeable mini-batch size to speed up the training. A main concern of me is whether the method could become a standard like data augmentation in image model and decaying learning schedule in almost every optimizer would do. If so, I admit it will be "accessible, scalable, and economical" like the paper said and maybe become a part of future video framework like [transforms](https://pytorch.org/docs/stable/torchvision/transforms.html) in pytorch (But I don't think it is a very sophisticated work to explore some deep aspects like many papers I have read before but no offense only my personal feeling:)