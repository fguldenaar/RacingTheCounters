# RacingTheCounters

## Omschrijving
Hierbij is mijn uitwerking voor de opdacht Racing the Counters.
Ik heb hier 2 varianten in verwerkt. De eerste is met behulp van synchronized. De tweede is door middel van reentrantlock.
Het concept van beide methodes hebben dezelfde doeleinde; het voorkomen/beperken van faalende threads.

```
synchronized{ //lock

} //unlock

```

De reentrantlock variant maakt gebruikt van de standaard Java library. In de `new ReentrantLock(true);` gedeelte kan er een true of false worden meegegeven.
Wanneer deze op `true` komt te staan wordt er een thread fairness toegepast. Iedere thread heeft een gelijke kans op zijn lock te bereiken.
Wanneer deze op `false` staat hebben threads geen gelijke kans om de lock te bereiken en bestaat er een hogere kans op thread starvation.
zal in een try catch block moeten worden verwerkt. 
```
ReentrantLock reentrantLock = new ReentrantLock(true);


        reentrantLock.lock();

        try{
            System.out.println(Thread.currentThread().getName() + ": " + counter);
            counter++;

        } catch (Exception e) {
            e.printStackTrace();
        }finally {
            reentrantLock.unlock();
        }

```
