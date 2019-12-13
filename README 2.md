# 09LabCT

12-12-19 NOTES

Virtuals are things that can be accessed by models

## dog.js

const mongoose = require('mongoose ')

const schema = new mongoose.Schema({

})

modules.export('Dog', schema)

## sandbox.js

const Dog = require(./dog.js)

async fucntion play() {
    const dog = await Dog.create();

}

play()
.then(() => console.log('done'));

## dog.js

.Schema({
    name: {
        string
    }
    dob: {
            type: date
    }
    weight: {
        type: String
    }
})

## sandbox
** in async fuction play()

const dog = await Dog.create({
    name 
    dob
    weight
})

## dog.js -- so this gets us the age even though no age exists in mongoDb
schema.virtual('age).get(function() {
    const now = new Date();
    this.dob.getFullYear() - thihs.dob.getFullYear(); 
})

*** arrow functions dont have a this. that they can inheret. so the above 55 line code couldn't run if 53 line was an arrow function

** a good use for virtuals is userAuth so it isn't stored in teh dB

so console.log(dog.age) actually envokes a function even though 

## sandbox.js

console.log(dog.toJSON({ virtuals: true }))
console.log(dog.age

##dog.js

---under schema.virtual('age')

.set(function(val) {
** with age, change birth year based on a change in age?**
cosnt thisBirthYear = this.dob.getFullYear(); 
const diff = val - this.age
this.dob.setYear(currentBirthYear - diff);
}); 

## sandbox.js

 dog.age = 7

 now dob for dog goes down two years


 *** so overall, this is beign done, the .get and .set fucntions, to deal in the future with passworlds which are hashed in the virtual.


 **so correctign information perhpas for a virtually created field is another reason to use the .set. 

 ## Dog.test.js

 const Dog = requrie('./Dog);
 describe('Dog model', () => {
     it('has an age virtual', () => {
         const go = new Dog({
             name: 
             dog: new Date (...
             weight: '20..'

         })
         expect(dog.age).toEqual(5)

         ** or for .set, we are just adding the age below, and everything above is the same

         dog.age = *new age here like 7

         or expect (dog.dob.toEqual( new Date( .. this is two less)))
     })

 })


## sandbox 2
** gonna have to look at this code, not clear
check book.js line 17 etc. 
this is populate virtuals. 
____________________
express middleware

when we attach middleware we use typeical 

app.use(fn)

fn's signature is req, res, next => { }

app.put/post/.. method name .. these are all just different types of middleware. 

## app.js

app.use((req, res, next) = > {
console.log('i am inside middleware') < --- this fires first
next(); 
});

app.use((req, res, next) = > {
console.log('second middleward') < --- this fires second. it only runs if you call next in the first. 
});

app.get('/', (req, res, next) => {
    res.end('we made it') <------ so this only runs as well when we invoke next(); in the middleware before 
})

app.use(err, req, res, next ) => {
    consoel.log(err); 

}

we will net the error message that is located in the previous middleware next('this error here ')

now we can add in this app.use

res.status(503).send({
    messageerr
})

 