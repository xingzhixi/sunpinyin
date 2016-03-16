(X\_0 .. X\_i) <smoothed probability P(X\_i|X\_0...X\_i-1> <backoff weight> (lower-order level index for backoff node)

E.g., 自己喜欢 女人 0.000623322849 0.363099098206 (1,33815)

  * 自己喜欢 女人: is the bigram
  * 0.000623322849: smoothed probability of P (女人 | 自己喜欢)
  * 0.363099098206: backoff weight, bow(自己喜欢)
  * (1, 33815): the index of 自己喜欢 record, level 1 and NO. 33815 element

For non-threaded ARPA files, the level index for backoff nodes would not be present.