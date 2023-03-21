In order to limit the growth of its population, the Chinese government decided to limit families to having just one child. An alternative that was suggested was the "one-son" policy: as long as a woman has only female children she is allowed to have more children. One concern voiced about this policy was that no family would have more than one son, but many families would have several girls. This concern lead to our question: How would the one-son policy affect the ration of male to female births?

From Elementary Probability for Applications, By Rick Durrett
---
My thought: Why would it affect the female-male ratio? The natural ratio of sex should be equals since you don’t kill girls to break the balance. (Well, sadly maybe it’s not the case, pretend it’s true for now). Let’s see the book’s explanation.
---
To simplify the problem we assume that a family will keep having children until it has a male child. Assuming that male and female children are equally likely and the sexes of successive children are independent, the total number of children has a geometric distribution with success probability p =1/2, so by the previous example the expected number of child is 1/p =2 (E of geometric distribution is 1/p). There is always one male child, so the expected number of female children is 2-1 = 1.
 
Does this continue to hold if some families stop before they have a male child? Consider for simplicity the case in which a family will stop when they have a male child or a total of three children. There are 4 outcomes:
 
P(M) = 1/2; P(FM) = 1/4; P(FFM) = 1/8; P(FFF) = 1/8;
 
The average number of male children is  1/2 + 1/4 + 1/8 = 7/8, while the average number of female children is 1*(1/4) + 2*(1/8) + 3*(1/8) = 7/8;
 
The last calculation makes the equality of the expected values look like a miracle, but it is not, and the claim holds true if a family with k female children continues with probability Pk and stops with probability 1-Pk. To explain this intuitively, if we replace M by +1 and F by -1, then childbirth is a fair game. For the stopping rules under consideration the average winnings when we stop have mean 0; that is, the expected number of male children equals the expected number of female children.
