# ml-pet-event-classification-data

The data is structured in sets of four rows of length 21, where each row has data (space-delimited):

x1c, y1c, z1c, x1p, y1p, z1p, x2c, y2c, z2c, x2p, y2p, z2p, e1c, e1p, e2c, e2p, theta1_pos, theta2_pos, theta1_e, theta2_e, deltaPhi, label
 
Here, 1 means gamma1, 2 means gamma2, c means Compton, p means photoelectric absorption, and e means energy. 
There are 2 thetas for each gamma: theta#_pos is a position-derived angle and theta#_e is an energy-derived angle.
Each of the four rows has a different configuration of hits (and thus angles). For example, if row 1 is the true configuration, row 2 would be if we swapped the hit coordinates of gamma1's c and p interactions.

So, reading in one sample should yield, after separating the label column:
 [[ x1c, y1c, z1c, x1p, y1p, z1p, x2c, y2c, z2c, x2p, y2p, z2p, e1c, e1p, e2c, e2p, theta1_pos, theta2_pos, theta1_e, theta2_e, deltaPhi]     label,
 [ x1c, y1c, z1c, x1p, y1p, z1p, x2c, y2c, z2c, x2p, y2p, z2p, e1c, e1p, e2c, e2p, theta1_pos, theta2_pos, theta1_e, theta2_e, deltaPhi]     label,
 [ x1c, y1c, z1c, x1p, y1p, z1p, x2c, y2c, z2c, x2p, y2p, z2p, e1c, e1p, e2c, e2p, theta1_pos, theta2_pos, theta1_e, theta2_e, deltaPhi]     label,
 [ x1c, y1c, z1c, x1p, y1p, z1p, x2c, y2c, z2c, x2p, y2p, z2p, e1c, e1p, e2c, e2p, theta1_pos, theta2_pos, theta1_e, theta2_e, deltaPhi]     label]
