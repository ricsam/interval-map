# interval-map
Utility library for working with interval data structures in javascript

## usage
This tool can be used to read and write subsets of larger data sets.
It is also suitable for locating missing data and adding new data without making unnessesary operations. It will keep your large sets organized and easily accessible.

### example

### about
This library will index your data into an interval tree structure.

## API

### constructor
```javascript
type options = {
    inclusive: boolean,
    inclusiveRight: boolean,
    inclusiveLeft: boolean,
    splittingDensity: number,
    /*
        splittingDensity = [0, 1],
        This will set the subIntervalSize based on the length of the
        dataset.
        given an interval containing data of range [0, 1000], a
        splittingDensity of 0.1 will create 10 sub intervals of
        interval [n+0, n+100] n = 0, 100, 200, ..., 900.

        Thus, to find data corresponding to the in-range value of
        e.g. 550, the top-level containing interval of [500, 600]
        will be found in 6 steps. Thereafter, as the data of [500,
        600] is 10 instances of [u+500, u+510], u = 0, 10, 20, ...,
        90 the second top-level interval containing, [550, 560],
        will be found in yet another 6 steps. Thus the total amount
        of steps needed to find the data was reduced from 500 to 12.
    */
    subIntervalSize: number,
    /*
        This will override the splittingDensity and instead will be
        a number which will be more dependant on your data. This
        will specify the sub-interval length.
    */
};
new Imap(/* options */);
```

### findIntervalGaps
```javascript
const Imap = require('interval-map');

const intervals = new Imap([0, 2], [10, 15]);
intervals.findIntervalGaps([1, 12], {inclusive: false});
// [3, 9]
intervals.findIntervalGaps([1, 12], {inclusive: true});
// [2, 10]
intervals.findIntervalGaps([1, 12], {inclusiveRight: true});
// [3, 10]
intervals.findIntervalGaps([1, 12], {inclusiveLeft: true});
// [2, 10]
```
`inclusiveRight` and `inclusiveLeft` have priority over `inclusive` and they can be used in combination.

### Argument
```javascript
const imap = require('interval-map');
const 
```