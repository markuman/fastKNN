# fastKNN

Loop-Free KNN algorithm for GNU Octave and Matlab

* Origin: https://git.osuv.de/m/fastknn
* Pull Mirror: https://gitlab.com/markuman/fastknn
* Push Mirror: https://github.com/markuman/fastknn

# Dataset

Dataset taken from http://www.jiaaro.com/KNN-for-humans/


    dataset = [
      %weight, color, # seeds, type
      303,     3,      1, 1;
      370,     1,      2, 2;
      298,     3,      1, 1;
      277,     3,      1, 1;
      377,     4,      2, 2;
      299,     3,      1, 1;
      382,     1,      2, 2;
      374,     4,      6, 2;
      303,     4,      1, 1;
      309,     3,      1, 1;
      359,     1,      2, 2;
      366,     1,      4, 2;
      311,     3,      1, 1;
      302,     3,      1, 1;
      373,     4,      4, 2;
      305,     3,      1, 1;
      371,     3,      6, 2;
    ];

    % lousy mapping
    fruit = {'Banana', 'Apple'}; 
    color.index = {'red', 'orange', 'yellow', 'green', 'blue', 'purple'};
    color.red       = 1;
    color.orange    = 2;
    color.yellow    = 3;
    color.green     = 4;
    color.blue      = 5;
    color.purple    = 6;

    UF1 = [301, color.green, 1];
    UF2 = [346, color.yellow, 4];
    UF3 = [290, color.red, 2];


Play with the Dataset.

	normalize = @(x) (x - min(x)) / max((x - min(x))); % reduce by smallest value

# usage

`[classified, k, dist, idx] = fastKNN(trained, unknown, k, distance)`  

* `classified` - result of KNN
* `k`  
  * nargin: the defined `k` 
  * nargout: information which `k` was taken _(...when `k` was automatically determined!)_
* `dist` - sorted calculated distances
* `idx`  - Index to map sorted distances `dist` to input dataset `trained`
* `distance` - default = 2
  * `distance == 2`: **Minkowski becomes equal Euclidean**
  * `distance == 1`: **Minkowski becomes equal city block metric**
  * `else`: **Minkowski distance** -  https://en.wikipedia.org/wiki/Minkowski_distance


## default with Euclidean distance and automagical determine of `k` 

	>> fastKNN(dataset, UF1)
	ans =
     1
	>> fruit(ans)
	ans = 
	'Banana'





