Monads
======

bind ("action")
---------------

monadic "apply" operator

Bekommt einen monadischen Wert.
Entpackt ihn (regulärer, nicht-monadischer Wert).

and passes that value as the input to the monadic function, which produces a monadic
value ("action") as its final result.

    (>>=) :: m a -> (a -> m b) -> m b
    (=<<) :: (a -> m b) -> m a -> m b

composition
-----------

    (>=>) :: (a -> m b) -> (b -> m c) -> (a -> m c)
    (<=<) :: (b -> m c) -> (a -> m b) -> (a -> m c)

return
------

return nimmt einen Wert und erzeugt einen monadischen Wert

    return :: a -> m a

Profiling
---------

enable profiling in cabal (~/.cabal/config)
reinstall packages
compile source with ghc -prof source.hs

    ghc -prof -rtsopts --make Main.hs
    ./Main +RTS -hc -RTS
