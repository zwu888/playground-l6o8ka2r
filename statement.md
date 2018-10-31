# description: 
 deleting NULL pointers have no effect.  deleting a pointer to a base class which points to a derived object is legal assuming the base destructor is virtual. deleting an array of objects using a base class pointer is undefined.
```C++ runnable
struct Foo
{
   virtual ~Foo() {}
   };

struct Bar : public Foo
  {
  };
 
 int main(int argc, char** argv)
 {
   Foo* f = new Bar;
   delete f;
   f = 0;
   delete f;

   Foo* fa = new Bar[10];
   delete [] fa;
   fa = 0;
   delete fa;

   return 0;
}
```

