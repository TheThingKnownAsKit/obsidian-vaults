![[03 Decision Trees Part 2.pdf]]

## ID3 Algorithm
The basic idea is as follows:
- Calculate how "well" each feature can separate the data
- Select the feature that maximally separates data as the new node
- Recursively, split each branch on the remaining features based on how well they each perform
Use entropy to model uncertainty about an outcome
$$Entropy(X)=-\sum^n_{i=1}p(x_{i})*\log_{b}(p(x_{i}))$$

We need to determine which feature maximally separates our data, so we will use the <mark style="background: #ADCCFFA6;">gain</mark> function
$$Gain(X,F)=Entropy(X)-\sum_{v\ \epsilon\ values(F)}\frac{|X_{v}|}{|X|}*Entropy(X_{v})$$

### ID3 Example

| Weather | Age      | Ice Cream? |
| ------- | -------- | ---------- |
| Hot     | Under 30 | Yes        |
| Hot     | Over 30  | No         |
| Cold    | Under 30 | Yes        |
1. We need prior entropy
$$Entropy(Ice\ Cream)=-P(Yes)*\log_{2}(P(Yes))-P(No)*\log_{2}(P(No))$$
$$=-\frac{2}{3}*\log_{2}\left( \frac{2}{3} \right)-\frac{1}{3}*\log_{2}\left( \frac{1}{3} \right)=0.92$$
2. We need information gain
$$Gain(Ice\ Cream, Weather)=Entropy(Ice\ Cream)-\sum_{v\ \epsilon\ values(Weather)}\frac{|Ice\ Cream_{v}|}{|Ice\ Cream|}*Entropy(Ice\ Cream_{v})$$
$$=0.92-\frac{|Ice\ Cream_{Hot}|}{|Ice\ Cream|}*Entropy(Ice\ Cream_{Hot})-\frac{|Ice\ Cream_{Cold}|}{|Ice\ Cream|}*Entropy(Ice\ Cream_{Cold})$$
$$=0.92-\frac{2}{3}*Entropy(Ice\ Cream_{Hot})-\frac{1}{3}*Entropy(Ice\ Cream_{Cold})$$
$$=0.92-\frac{2}{3}*1-\frac{1}{3}*0=0.25$$
3. Do the same for age gain
$$=0.92-\frac{2}{3}*0-\frac{1}{3}*0=0.92$$
1. Select the best feature out of these two. Between a gain of 0.25 (Weather) or 0.92 (Age), you should select age. Since there is only two variables, this is where it ends