[![Build Status](https://travis-ci.org/ibrahimyilmaz/ArchData.svg?branch=master)](https://travis-ci.org/ibrahimyilmaz/ArchData)
ArchData
=======

ArchData provides two missing LiveData of Android Lifecycle Component.

MutableLiveData shares only last state to its new observers when they start to observe.

But in some cases, either these observers may want to do fresh start or they want to get all previous states.

PublishLiveData and ReplayLiveData types are extensions of MutableLiveData.

Basically:

* PublishLiveData is MutableLiveData, which only notify its observers if there is an event after their starting of observation.
* ReplayLiveData is MutableLiveData, which only notify its observers for all previous events happened before their observation starts.


Usage
-----

 *  **`PublishLiveData`**

    LiveData that, once an `Observer` has subscribed, emits all subsequently observed items to the
    subscriber.

    ```kotlin
    val liveData = PublishLiveData<String>();
    // observer1 will receive all events
    liveData.observe(lifeCycleOwner,observer1);
    liveData.postValue("one");
    liveData.postValue("two");
    // observer2 will only receive "three"
    liveData.observe(lifeCycleOwner,observer2);
    liveData.postValue("three");
    ```

 *  **`ReplayLiveData`**

    LiveData that buffers all items it observes and replays them to any `Observer` that subscribes.

    ```kotlin
    val liveData =  ReplayLiveData<String>();
    liveData.postValue("one");
    liveData.postValue("two");
    liveData.postValue("three");
    // both of the following will get the events from above
    liveData.observe(lifeCycleOwner,observer1);
    liveData.postValue(lifeCycleOwner,observer2);
    ```

Download
--------

Coming soon...


License
-------

    MIT License

    Copyright (c) [2019] [IBRAHIM YILMAZ | cs.ibrahimyilmaz@gmail.com]

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.
