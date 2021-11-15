# Stack-Overflow-Developer-Survey-Analysis

### Color palette used in this notebook
#24477f : Mck deep blue  
#0892d0 : Mck electric blue  
#66b3ff : light blue  
  
mck_color2 = sns.color_palette(['#0892d0', '#24477f'])  
mck_color = sns.blend_palette(['#0892d0', '#24477f','black'],9)    
mck_color12 = sns.blend_palette(['#0892d0', '#24477f','black'],12)  
mck_color25 = sns.blend_palette(['#41aad9','#0892d0', '#24477f','black'],25)  
sns.color_palette('Blues')  
sns.color_palette(mck_color2)  
![color grid](https://user-images.githubusercontent.com/86042628/141689201-47927864-c7bb-4861-aa39-678b0178107a.PNG)

### Functions used in this Notebook
1.  **Creating a function for Feature Engineering**

def split_multicolumn(col_series):  
    result_df = col_series.to_frame()  
    options = []  
    # Iterate over the column  
    for idx, value  in col_series[col_series.notnull()].iteritems():  
        # Break each value into list of options  
        for option in value.split(';'):  
            # Add the option as a column to result  
            if not option in result_df.columns:  
                options.append(option)  
                result_df[option] = False  
            # Mark the value in the option column as True  
            result_df.at[idx, option] = True  
    return result_df[options]  
    
   // delimiters like :,/
