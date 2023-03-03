A few additionnal info that may or may not be useful :

The main idea during the devellopment of the full project was to make each event as simple as possible.
It means that there where a lot of small events, but it allows your project to be (more easily) proved by Rodin.
The goal was to have a 100% proved program without making any proof by hand.

When you want a new version of an already existing event in your new machine, you can refine events using this syntax :
```
event event_name_1 refines event_name_1
where
    @grd1_1: < old guard >
    @grd2_2: < additional guard >
then
    @act1_1: < old post condition >
    @act2_2: < additional post condition >
end
```

When you don't want to make a new version of an already existing event in your new machine, you can extend events using this syntax :
```
event event_name_1 refines event_name_1
where
    @grd1_1: <old guard >
    @grd2_2: <additional guard >
then
    @act1_1: <old post condition >
    @act2_2: <additional post condition >
end
```

The more complex instruction I used is the `:| (become such that)` operator, here's how to use it :
```
event event_name_1
where
    @grd1_1: < guard >
then
    @act1_1: var1 :∣ var1' ∈ < type > ∧ (< conditionA > ⇒ < actionA >) ∧ (< conditionB > ⇒ < actionB >)
end
```
where `< type >` is a set (that may have been defined in a context file),
where `< conditionX >` is a boolean expression,
where `< actionX >` is an action (typically an assignation) on `var1'`, which represents the new value of `var1`
