# Blogpost
hdfs is the hadoop distributed filesystem, dfs runs the filesystem command on the file in hadoop. 

# what i did
First, I pulled 100.txt from the given repository and put it in a variable called input. Then I created a file called WordCount.java w
with vi editor and ran it with as input the 100.txt file and output the result in a file named output. 
Using bin/hadoop fs -cat hdfs://localhost:9000/user/root/output/part-r-00000, i displayed the output to obtain the results of the
wordcount program. 

# Questions
    1. What happens when you run the Hadoop commands (hdfs dfs etc.) in the first week’s part of the tutorial?
hdfs is the hadoop distributed filesystem, dfs runs the filesystem command on the file in hadoop. Running these allows you to
run the hadoop commands on files, so that the files can be read by hadoop.

    2.How do you use mapreduce to count the number of lines/words/characters/… in the Complete Shakespeare?
you change the wordcount.java file to count lines/sentences/characters instead of words. Mapper function needs to map the desired 
text property so that the reducer can can count. For words you change it so that every word is mapped on the same key:
public static class TokenizerMapper
       extends Mapper<Object, Text, Text, IntWritable>{

    private final static IntWritable one = new IntWritable(1);
    private Text word = new Text();

    public void map(Object key, Text value, Context context
                    ) throws IOException, InterruptedException {
      StringTokenizer itr = new StringTokenizer(value.toString());
        while(itr.hasMoreTokens()){
        itr.nextToken();
        context.write(word, one);
        }

    }
  }
  There are 966997 words.
for lines, you change the code so that every line is mapped on the same key:
public static class TokenizerMapper
       extends Mapper<Object, Text, Text, IntWritable>{

    private final static IntWritable one = new IntWritable(1);
    private Text word = new Text();

    public void map(Object key, Text value, Context context
                    ) throws IOException, InterruptedException {
        context.write(word, one);
    }
  }

There are 147838 lines.
For characters:
public static class TokenizerMapper
       extends Mapper<Object, Text, Text, IntWritable>{

    private final static IntWritable one = new IntWritable(1);
    private Text word = new Text();

    public void map(Object key, Text value, Context context
                    ) throws IOException, InterruptedException {
             String line = value.toString();
        char[] carr = line.toCharArray();
        for (char c : carr) {
            context.write(new Text(), new IntWritable(1));
        }
        }
      }
There are 5545144 characters.
    3.Does Romeo or Juliet appear more often in the plays? Can you answer this question making only one pass over the corpus?
You change the map method to output all cases of romeo and juliet to their respective keys, ignoring special cases. 
 public static class TokenizerMapper
       extends Mapper<Object, Text, Text, IntWritable>{

    private final static IntWritable one = new IntWritable(1);
    private Text word = new Text();

    public void map(Object key, Text value, Context context
                    ) throws IOException, InterruptedException {
             StringTokenizer itr = new StringTokenizer(value.toString());
      while (itr.hasMoreTokens()) {

        word.set(itr.nextToken());

        if (word.toString().replaceAll("\\W","").equals("Romeo")){
                context.write(new Text("Romeo"), one);
                }
        if (word.toString().replaceAll("\\W","").equals("Juliet")){
                context.write(new Text("Juliet"),one);
        		}
        	}
        }
    }


Romeo is mentioned 126 times, whereas Juliet is mentioned 63 times.
So Romeo appears more times.
