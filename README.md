# rblineprof

```
% ruby -C ext extconf.rb
% make -C ext
% ruby test.rb 
       | $:.unshift 'ext'
       | require 'rblineprof'
       | 
       | per_line = lineprof(__FILE__) do
     1 |    1000.times do
       | 
   269 |      1*2*3
   243 |      4*5*6
   840 |      7*8*9*10*11*12*13*14*15
   204 |      2**32
   655 |      2**128
       | 
       |   end
       | end
       | 
       | File.readlines(__FILE__).each_with_index do |line, num|
       |   if sample = per_line[num+1]
       |     printf "% 6d |  %s", sample, line
       |   else
       |     printf "       | %s", line
       |   end
       | end
```

## Other profilers

* [PLine](https://github.com/soba1104/PLine) line-profiler for ruby 1.9
* pure-ruby [LineProfiler](http://blade.nagaokaut.ac.jp/cgi-bin/scat.rb/ruby/ruby-talk/18997?help-en) for ruby 1.6