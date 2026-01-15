- [Why AI slop?](#orgeaea0ec)
  - [The Subtle Overloading of everyday speach](#orgf73a047)
  - [The Intuitive possibility of a Proper Unification](#orgd9e85c2)
  - [Uniform pattern-matching everywhere](#org9fd8638)
  - [A sum of products and product of sums](#org9ca718c)
  - [The algorithm charting &ldquo;primitives&rdquo;](#orgc2d2319)
  - [DAGs](#org2c17e51)



<a id="orgeaea0ec"></a>

# Why AI slop?

The decision to use AI was due to its ability to overcoming the fundamental problem of being quickly overwhelmed and frustrated to exhaustion by the need to parse through narcissistic graphomania of mere impostures or plowing through low-effort verbiage of Pakt-style shitbooks (literally), which are, at best, a slightly edited copy-pasta from crappy online resources.

The slop, while being full of subtle hallucinations, have almost no distractions and, at least in theory, converges to some common denominator on the topic by the definition (of the algorithms being used).

Once you get the habit of not taking the generated slop quite literally, but as a general drift in the right direction (hopefully, toward &ldquo;semantic&rdquo; fixed-point, which is exactly what the Gradient Descent does), the inevitable hallucinations and plain errors become tolerable. Much more tolerable that an emotionally charged social media crap or a pretensions verbiage of an over-confident narcissistic mediocrity.


<a id="orgf73a047"></a>

## The Subtle Overloading of everyday speach

Having not yet clearly articulated *intuitive* understanding is not enough, but one cannot render into a precise wording because it is not &ldquo;intuitively well-formed&rdquo; yet.

For example, a &ldquo;central&rdquo;, every-day, (every-minute!) notion, captured in English by the word `and` has at least 4 different overloads, depending on the immediate context.

-   `andAlso` (present in the same locality)
-   `andThen` (with the subtle order &#x2013; nesting of events)
-   formally defined logical connective `AND` (by a truth-table)
-   and the way to build a continuity of a long sentence
-   simultaneously (at the same time), which is, if you think for a second, is another way to say &ldquo;present at the same locality&rdquo; (hi, PhDs in Quantum phisics).

This is what mathematicians means when they say that the [formal] written language of mathematics has to be unambiguous &#x2013; one not just have to define the terms before using them, but also define how properly use (which particular overload) of `AND` and `OR` (one has to explicitly chose &ldquo;inclusive&rdquo; vs. &ldquo;exclusive&rdquo; overload) .


<a id="orgd9e85c2"></a>

## The Intuitive possibility of a Proper Unification

The unification *feels* &ldquo;just right&rdquo; when one intuitively &ldquo;sees&rdquo; that some specialized notions (or syntactic forms) have a common &ldquo;underlying&rdquo; generalized form.

For example, a function defined as a set of individual *clauses* (not even a list, because they are proper disjoint union at the level of abstract interfaces) and each clause &ldquo;naturally&rdquo; defines a distinct *partial function* which implicitly partition the domain and range (and proper sum-types define just such kind of explicit partitions).

Another well-known abstract notion is that `let` is &ldquo;just&rdquo; a `lambda` with in-place application, and *nested lets* correspond to nested lambdas, and `let*` captures the outer bindings just like a proper closure would.

None of this is by accident, of course, intuition &ldquo;knows&rdquo; this for a long time.

Form this, less obviously, can be realized that a singe `let` is just an anonymous single function clause, with an implicit scope of a proper closure.


<a id="org9fd8638"></a>

## Uniform pattern-matching everywhere

Another observation is that a *conditional expression* has to be one-and-the-same &#x2013; a properly generalized `case` analysis, with the very same (but inverse) multi-clause structure as a function.

From this one could see that it shall not be just a `case` expression, but the even more germinal `match` expression, which, again, a union of disjoint clauses (a set) and it does pattern-matching local bindings.

This is, indeed, a proper *inverse* of what a parameterize Data-constructor does. Category Theorists showed this formally, but &ldquo;we&rdquo; see this all the time intuitively.

There another, &ldquo;deeper&rdquo; realization at the level of abstract machines &#x2013; the `case` &ldquo;induction&rdquo; is all you need, and, again, a function is just a [single] individual clause.


<a id="org9ca718c"></a>

## A sum of products and product of sums

These notions arise &ldquo;naturally&rdquo; from nesting (parameterization) of the Popper Algebraic Data Types. The Category theorists (hi, Bartosz) have demonstrated that one is a *dual* of the other

The important part is not way too abstract &ldquo;duality&rdquo; itself, but *nesting*, so each *clause* could have a *nested set* (disjoint union) of clauses, and that a &ldquo;singe&rdquo; product is an &ldquo;one item sum&rdquo; (and single-clause sum is just as good as a product of one)

Again, one does not come to realize all thins in an instant, articulated this clearly &#x2013; it takes years.


<a id="orgc2d2319"></a>

## The algorithm charting &ldquo;primitives&rdquo;

There are lot more of such hidden &ldquo;correspondences&rdquo; or observed &ldquo;isomorphisms&rdquo;, of course, none of which are mere accidents.

Oldfags can&rsquo;t remember, newfags do not know that there were special kinds of &ldquo;rulers&rdquo; for drawing algorithmic diagrams (algorithm charting),

When one examines such diagrams, one will notice that there are only 3 universal structural elements - a &ldquo;fork&rdquo;, a &ldquo;join&rdquo;, and a &ldquo;step [forward]&rdquo;.

Unsurprisingly, the very same structural &ldquo;primitives&rdquo; underlay every Electrical Engineering schematic in the whole world.


<a id="org2c17e51"></a>

## DAGs

One more step, and one realizes that a DAG is a common underlying structure behind formal logic, algorithms (meet the Curry-Howard isomorphism once again), and thus any computation (where recursion is used instead of imperative looping, so it remains a proper DAG).

The crucial part, however is, again, an &ldquo;unlimited&rdquo; nesting &#x2013; the notion that &ldquo;inside&rdquo; every clause could be another set of clauses, and that the &ldquo;direction&rdquo; is not optional and cannot be reversed on whim (as in *apparent* &ldquo;duality&rdquo; of sums and products).

This, basically, concludes everything I did here &#x2013; formalized my long-standing *intuitive understanding* with the help of a state-of-the-art slop generator trained on the right (old-school) texts .

Everything else just &ldquo;naturally follows&rdquo; from these realizations (discoveries).
