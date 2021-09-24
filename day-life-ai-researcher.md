# WIP: A "day" in life of an experimental AI researcher

TLDR; A journey through the life of an "AI" research project. The boring part that never gets disclosed, fighting the dragon.

It's cool to see people disclosing tricks to tame deeplearning models. What about odd or unresolved 🧩? Here you get one.

Situation: I'm doing a hybrid conv-net & Transformer.

1. It was crucial to ensure that conv-net alone output smth sensible.

    Fix data issues, set KPIs, yada yada ([Andrej-tips](), [FullStack ML-Engineer](), etc.).

2. Then, the fun part for those who care about be cool-kids, adding the Transformer.

    It took > 15 experiments to tame the new beast. Typical stuff (regularization, read implementation details of a bunch of papers) and of-course:

    - access to GPUs 🙂

    - patience and coffee

3. OK, I improve the KPI by relevant tolerance margin.

    `You: Wait, was that? Isn't it enough to see 0.1-0.5%?`

    Mmm, if you wanna fool urself and end up with a Frankenstein and gazillion wheels maybe.

    `You: OK. How to set that margin, an ANOVA test?`

    too fancy. The avg reviewer doesn't know what ANOVA & p-value mean 🤭, they only pay attention that your stuff fits the bandwagon 🤫.
  
    `You: so?`

    Just run the same config a couple of times with some augmentations & calibrate ur 👀 KPI variations. If you can, submit it to a test server

4. After trying a bunch of stuff, I hit a roof. Thus, I put the hat of Sherlock and start debuging. Found a couple of odd things!
  
5. Aja, the input to my transformer comes from a ReLU.

    `You: but there is a KQV projection before attention. no?`

    Sure, but also a residual connection. Let's add a linear projection layer to map the embedding learned by the ConvNet.

    `You: OK and?`
 
    Perfomance drop!
