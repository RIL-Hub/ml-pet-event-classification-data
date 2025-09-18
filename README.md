# ml-pet-event-classification-data

The data is structured in sets of four rows of length 21, where each row has data (space delimited):
> x1c, y1c, z1c, x1p, y1p, z1p, x2c, y2c, z2c, x2p, y2p, z2p, e1c, e1p, e2c, e2p, theta1_pos, theta2_pos, theta1_e, theta2_e, deltaPhi, label
 
Here, 1 means gamma1, 2 means gamma2, c means Compton, p means photoelectric absorption, and e means energy. There are 2 thetas for each gamma: theta#_pos is a position derived angle and theta#_e is an energy derived angle.
Each of the four rows has a different configuration of hits (and thus angles). For example, if row 1 is the true configuration, row 2 would be if we swapped the hit coordinates of gamma1's c and p interactions.
There are 802,510 training samples (sets of 4 rows). Half of these are Trues (one of the configurations is accurate and has a label of 1). The other half are Randoms (all configurations are wrong and all labelled with 0).

So, reading in one sample should yield, after seperating the label column:
> [[ x1c, y1c, z1c, x1p, y1p, z1p, x2c, y2c, z2c, x2p, y2p, z2p, e1c, e1p, e2c, e2p, theta1_pos, theta2_pos, theta1_e, theta2_e, deltaPhi]     label,
> 
>  [ x1c, y1c, z1c, x1p, y1p, z1p, x2c, y2c, z2c, x2p, y2p, z2p, e1c, e1p, e2c, e2p, theta1_pos, theta2_pos, theta1_e, theta2_e, deltaPhi]     label,
> 
>  [ x1c, y1c, z1c, x1p, y1p, z1p, x2c, y2c, z2c, x2p, y2p, z2p, e1c, e1p, e2c, e2p, theta1_pos, theta2_pos, theta1_e, theta2_e, deltaPhi]     label,
> 
>  [ x1c, y1c, z1c, x1p, y1p, z1p, x2c, y2c, z2c, x2p, y2p, z2p, e1c, e1p, e2c, e2p, theta1_pos, theta2_pos, theta1_e, theta2_e, deltaPhi]     label]

The way the data is structured, if the sample is true, configuration/row 1 will be the true configuration with label 1. So, the rows must be shuffled. I imagine this would have already been done prior to each training epoch, but just making sure.
Further, the first half of the samples are the Trues and the later half are the Randoms. So samples will also need to be shuffled, which again I imagine would already be done.
Augmentation of the data is tricky because the angles are dependent on the interaction locations and interaction energies.

To reiterate how we discussed the network will function.
> Input: a set of four configurations, by row
> 
> Output: 4-vector containing the probability of each configuration being True. Follow with a softmax for classification?
