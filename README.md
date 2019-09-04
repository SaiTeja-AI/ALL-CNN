# ALL-CNN
<h1>introduction</h1>
<p>cifar-10 famous data set which contain ten different types of images like cats,dogs,horse,airoplane etc ,which are low resolution 32x32 with 3 channels which pose challenge to classification if we use normal combination of convolutional layers and max pooling layers along with data agumentation ae can achieve graetly 65% accuracy.</p>
<p>people came up with many techniques and approaches one of the technique is Striving for Simplicity: The All Convolutional Net,they used 
only convolution layers with stride and expensive data augumentation techniques to achieve the accuracy of 95% still you can see it in the link <a href="https://benchmarks.ai/cifar-10">benchmarks.ai</a> </p>
<p>the original paper you can see in this link <a href="https://arxiv.org/abs/1412.6806">Striving for Simplicity: The All Convolutional Net</a> according to original paper they found that max-pooling on several image recognition benchmarks ,more elobaretly to say that pooling can be removed from a network without abandoning the spatial dimensionality reduction by replacing pooling layer by a normal convolution with  stride larger than one.</p>
<h2>Architectuer</h2>
<p>before going to architectuer if we use convolutional layers instead of maxpooling it increases the number of training parameters so we make use of small convolutional layers with k<5(kernel) which can greatly reduce the number of parameters in a network and thus serve as a form of regularization.Additionally, to unify the architecture further, we make use of the fact that if the image area covered by units in the topmost convolutional layer covers a portion of the image large enough to recognize its content (i.e. the object we want to recognize) then fully connected layers can also be replaced by simple 1-by-1 convolutions.This leads to predictions of object classes at different positions which can then simply be averaged over the whole image.so it has much less parameters than a fully connected layer.</p>
<p>Overall our architecture is thus reduced to consist only of convolutional layers with rectified linear non-linearities and an averaging + softmax layer to produce predictions over the whole image.</p>
<p> there are 3 varients which present with differnt kernel sizes only 5, 5 and 1 combined finally kernel size 3, i just used kernel size 3 and below table describes the network architectuer</p>
<table style="width:100%">
  <tr>
    <th> Model With Kernel Size 3</th>
  </tr>
  <tr>
    <th> Input 32x32 RGB Image</th>
  </tr>
  <tr>
    <th> 3x3 Convolutional Layers ,96 Relu </th>
  </tr>
  <tr>
    <th> 3x3 Convolutional Layers ,96 Relu </th>
  </tr>
  <tr>
    <th> 3x3 Convolutional Layers ,96 Relu, strides 2x2</th>
  </tr>
  <tr>
    <th> 3x3 Convolutional Layers ,192 Relu </th>
  </tr>
  <tr>
    <th> 3x3 Convolutional Layers ,192 Relu </th>
  </tr>
  <tr>
    <th> 3x3 Convolutional Layers ,192 Relu, strides 2x2</th>
  </tr>
  <tr>
    <th> 3x3 Convolutional Layers ,192 Relu</th>
  </tr>
  <tr>
    <th> 1x1 Convolutional Layers ,192 Relu,padding = 'same'</th>
  </tr>
  <tr>
    <th> 1x1 Convolutional Layers ,10 Relu,padding = 'same'</th>
  </tr>
  <tr>
    <th> Add Global Average Pooling Layer</th>
  </tr>
  <tr>
    <th> Finally add softmax layer</th>
  </tr>
</table>
<p> over all there are 1.3 million parameters are there to train the network it will take roughly 10 hours to train if we have gpu support so i did not train entier network instead i took already trained weights from this git hub 
<a href="https://github.com/PAN001/All-CNN/blob/master/all_cnn_best_weights_glorot_uniform.hdf5">click here</a> finally evaluated on test set got 90% accuracy with out any data augumentation technique.</p>
  
    
