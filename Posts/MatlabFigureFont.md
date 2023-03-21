#### Matlab Figure Plot Font Size Permanent Change

This is probably true only for Matlab version before 2019a

Tired of changing font size of titles and labels after plotting the figure in order to get intelligible characters in smaller scale? Matlab's recommended solution is to get the figure handle by calling

h = xlabel('blah'); set(h,'FontSize',10);

h = ylabel('blah');set(h,'FontSize',10);

h = title('blah');set(h,'FontSize',10);

However, I found invariably I had to change the font size since Matlab's default label size is too small when the figure scale needs to be shrunk  So to spare myself of writing the lines to set the property of figure object (labels and titles etc.) every time, I decide to change it permanently in Matlab's toolbox for plotting. The functions are located in:

.../toolbox/matlab/graph2d/...

After line of

if isempty(ax)

h = xlabel(gca,varargin{:}); %%/toolbox/matlab/graph2d/xlabel.m

or h = ylabel(gca,varargin{:});%%/toolbox/matlab/graph2d/ylabel.m

or h = title(gca,varargin{:});/toolbox/matlab/graph2d/title.m

Add in a line : set(h, 'FontSize',14);

Overwrite the original functions, done!
