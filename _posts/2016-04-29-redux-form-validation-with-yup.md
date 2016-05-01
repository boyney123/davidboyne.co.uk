---
layout: post

title: Using schemas to validate redux-forms

subtitle: "Using React, redux, redux-forms and yup to build forms and validation"

excerpt: "Yup with redux-form is pretty cool. Using schemas to validate our forms is very powerful...."

author:
  name: David Boyne
  twitter: boyney123
  bio: Just another developer
  image: ks.jpg
---

*TLDR; Yup with redux-form is pretty cool. Using schemas to validate our forms is very powerful. 
[Checkout the code here](https://github.com/boyney123/react-redux-form-yup-schema-example)*.

Working with forms and validation in single page applications can be a **pain**.

I have recently been writing a React application that requires form validation,
and found an interesting way to easily implement forms with validation using <code>redux</code>
, <code>redux-form</code> and <code>yup</code>.

In this post we will walk though how to create a basic form, apply <code>redux-form</code> to it and then apply our
<code>yup</code> schemas to valid it.

So, lets dive into some code.

##### Form.js

{% highlight js %}

import React from 'react';

class Form extends React.Component {
    render() {
        return (<form action="">

            <div>
                <label>Firstname:</label>
                <input
                    type="text"
                    placeholder="First Name"/>
            </div>

            <div>
                <label>Surname:</label>
                <input type="text" />
            </div>

            <div>
                <label>Email:</label>
                <input
                    type="email"
                    placeholder="Email"/>
            </div>

            <div>
                <label>Sex</label>
                <div>
                    <label>
                        <input
                            type="radio"
                            value="male" /> Male
                    </label>
                    <label>
                        <input
                            type="radio"
                            value="female" /> Female
                    </label>
                </div>
            </div>

            <button type="submit" >
                Submit
            </button>

        </form>);
    }
}

export default Form;

{% endhighlight %}

This is our basic Form component. A simple form with some fields to capture some basic information from our user. Nice and simple.

So lets add <code>redux</code> and <code>redux-form</code> to our application to start handling form data, validation and errors.

[*(This is not a redux or redux-form guide, if your interested in that please see the docs here)*](http://redux-form.com/5.2.3/).

## Adding validation

#### Form fields

First thing we do is define our fields for our form.
 

{% highlight js %}

const fields = ['firstName', 'lastName', 'email', 'sex'];

{% endhighlight %}


#### Synchronous Validation

Lets add some *(noddy)* validation. 

The <code>validate</code> function is called by <code>redux-form</code> with the values of our form *(which we have just setup)*. 
Here we can make sure they are valid then hydrate and return an error object if we have any problems.

{% highlight js %}

const validate = values => {

    const errors = {};

    if (!values.firstName) {
        errors.firstName = 'First name is required'
    }

    if (!values.lastName) {
        errors.lastName = 'Last name is required'
    }

    if (!values.email) {
        errors.email = 'Email is required'
    }

    if (!values.sex) {
        errors.sex = 'Sex is required'
    }

    return errors


};

{% endhighlight %}

#### Taking redux-form props and apply them to our form

Cool. So far we have a <code>validate</code> function and have defined our fields.

These fields are given to <code>redux-form</code>. Props are added to the component and the field objects are [decorated with <code>redux-form</code> functionality]((http://redux-form.com/5.2.3/#/api/props?_k=y7bc3u)).

With these new <code>props</code>  we need to map them back to our form.
Easist way to do this is to use the <code>spread operator</code> and apply them to our form.

##### define our fields
{% highlight js %}
const { fields: { firstName, lastName, email, sex } } = this.props;
{% endhighlight %}

##### spread props across our form
{% highlight js %}
<div>
	<label>First name:</label>
	<input
		type="text"
		placeholder="First name"
		{...firstName} />

	{firstName.touched
		&& firstName.error
		&& <div>{firstName.error}</div>}

</div>
{% endhighlight %}


#### Initialising redux-form

Last thing we need to do is simply wrap our component around the <code>reduxForm</code> function. 
This will setup our form for us, with the fields and validate function.

{% highlight js %}

export default reduxForm({
    form: 'userDetails',
    fields,
    validate
})(Form);

{% endhighlight %}


Great! Now we have validation and redux-form setup!

##### Form.js (With redux-form and validation)

{% highlight js %}

import React , {PropTypes} from 'react';
import { reduxForm } from 'redux-form';

//Define our form names for redux-form
export const fields = ['firstName', 'lastName', 'email', 'sex'];

/**
 * Our basic validation. Its abit noddy but just for demo purpose.s
 */
const validate = values => {

    const errors = {};

    if (!values.firstName) {
        errors.firstName = 'First name is required'
    }

    if (!values.lastName) {
        errors.lastName = 'Last name is required'
    }

    if (!values.email) {
        errors.email = 'Email is required'
    }

    if (!values.sex) {
        errors.sex = 'Sex is required'
    }

    return errors


};

class Form extends React.Component {
    render() {

        /* define our fields to bind to our form, from redux-form */
        const { fields: { firstName, lastName, email, sex }, handleSubmit } = this.props;

        return (<form onSubmit={handleSubmit(() => alert('success!'))}>

            <div>
                <label>First name:</label>
                <input
                    type="text"
                    placeholder="First name"
                    {...firstName} />

                {firstName.touched
                    && firstName.error
                    && <div>{firstName.error}</div>}

            </div>

            <div>
                <label>Last name:</label>
                <input
                    type="text"
                    placeholder="Last name"
                    {...lastName} />

                {lastName.touched
                    && lastName.error
                    && <div>{lastName.error}</div>}

            </div>

            <div>
                <label>Email:</label>
                <input
                    type="email"
                    placeholder="Email"
                    {...email} />

                {email.touched
                    && email.error
                    && <div>{email.error}</div>}

            </div>

            <div>

                <label>Sex</label>

                <div>
                    <label>
                        <input
                            type="radio"
                            {...sex}
                            value="male"
                            checked={sex.value === 'male'}/> Male
                    </label>
                    <label>
                        <input
                            type="radio" {...sex}
                            value="female"
                            checked={sex.value === 'female'}/> Female
                    </label>
                </div>

                {sex.touched
                    && sex.error
                    && <div>{sex.error}</div>}
                
            </div>

            <button type="submit" >
                Submit
            </button>

        </form>);
    }
}

Form.propTypes = {
    fields: PropTypes.object.isRequired,
    handleSubmit: PropTypes.func.isRequired
};

/**
 * Map our form to redux-form
 *
 * form -  The redux store will now have a section called userDetails which will store our form data
 *
 * fields - Tells redux-form the fields of our form and will spread its API across the objects (ready to be used in our form)
 *
 * validate - Sync function to call when we need to validate.
 */
export default reduxForm({
    form: 'userDetails',
    fields,
    validate
})(Form);



{% endhighlight %}



### Adding schemas for validation

We could stop there but validation kinda sucks right now, so lets add some better validation with schemas. Using [yup](https://github.com/jquense/yup).

<code>yup</code> allows us to define a validation schema for our form. We can tie it up to our form with a couple of easy steps.

Lets dive into the code and have a look at our schema.

##### form-schema.js
{% highlight js %}

/**
 * Using yup we can create our schemas for our form.
 */

import yup from 'yup';

export default yup.object().shape({

    firstName:      yup.string().required(),

    lastName:      yup.string().required(),

    //yup comes with some handy validation functions, as you can see email validation for us!
    email:      yup.string().email().required(),

    sex: yup.string().required()

});

{% endhighlight %}

You can probably read this quite easily and work out whats going on, its pretty straight forward.
We are making sure some of our fields are **required** and **valid**.

Next, lets tie this into our <code>redux-form</code>.


#### Using Object.keys to get fields

First we need to import our schema inside our Form.js. 

We no longer have to define our fields like this <code>['firstName', 'lastName'...]</code>
We can use <code>Object.keys()</code> to get our fields from our schema object. Pretty cool!

Everytime we change our schema in the future our fields will be bound to the changes, meaning less code for us to maintain.

{% highlight js %}

//Lets get our schema we created
import schema from './schemas/form-schema'

//Using Object.keys we can now get our redux-form fields from our schema!
export const fields = Object.keys(schema.fields);

{% endhighlight %}

####  Moving to asynchronous validation

<code>redux-form</code> allows us to validate our form <code>synchronously</code>, or <code>synchronously</code>. 

When we call <code>schema.validate()</code> on our schema, it returns a promise.
This means we have to refactor our form and validate it asynchronously.

When our schema is invalid <code>yup</code> will return an array of errors. We have to take <code>yups</code> errors and transform them into errors <code>redux-form</code> can understand.


{% highlight js %}

const asyncValidate = values => {

    return new Promise((resolve, reject) => {

        //Validate our form values against our schema
        schema.validate(values, {abortEarly: false})
            .then(() => {
                //form is valid happy days!
                alert('Your form is valid!')
                resolve();
            })
            .catch(errors => {

                //Yup errors > redux-form errors

                let rErrors = {};

                errors.inner.forEach(error => {
                    rErrors[error.path] = error.message;
                })

                reject(rErrors);

            })
    });

};

{% endhighlight %}


#### Setting up redux-form to use asyncValidation

Last thing we must do it remove synchronous validation, and replace it with our new asynchronous function.

{% highlight js %}

export default reduxForm({
    form: 'userDetails',
    fields,
    asyncValidate
})(Form);

{% endhighlight %}

#### React with redux-form and schema validation

Thats it! Our form is now using schemas to valid itself. No more writing horrid validation code around the place, we can just use
schemas to validate our form for us.

{% highlight js %}

import React , {PropTypes} from 'react';
import { reduxForm } from 'redux-form';

//Lets get our schema we created
import schema from './schemas/form-schema'

//Using Object.keys we can now get our redux-form fields from our schema!
export const fields = Object.keys(schema.fields);

/**
 * Now using Yup to validate our form with schema!
 */
const asyncValidate = values => {


    return new Promise((resolve, reject) => {

        console.log(values)

        //Validate our form values against our schema! Also dont abort the validate early.
        schema.validate(values, {abortEarly: false})
            .then(() => {
                //form is valid happy days!
                alert('Your form is valid!')
                resolve();
            })
            .catch(errors => {

                //form is not valid, yup has given us errors back. Lets transform them into something redux can understand.

                let reduxFormErrors = {};

                errors.inner.forEach(error => {
                    reduxFormErrors[error.path] = error.message;
                })

                //redux form will now understand the errors that yup has thrown
                reject(reduxFormErrors);

            })
    });

};

class Form extends React.Component {
    render() {

        /* define our fields to bind to our form, from redux-form */
        const { fields: { firstName, lastName, email, sex }, handleSubmit } = this.props;

        return (<form onSubmit={handleSubmit(() => alert('success!'))}>

            <div>
                <label>First name:</label>
                <input type="text" placeholder="First name" {...firstName} />
                {firstName.touched && firstName.error && <div>{firstName.error}</div>}
            </div>

            <div>
                <label>Last name:</label>
                <input type="text" placeholder="Last name "{...lastName} />
                {lastName.touched && lastName.error && <div>{lastName.error}</div>}
            </div>

            <div>
                <label>Email:</label>
                <input type="email" placeholder="Email" {...email} />
                {email.touched && email.error && <div>{email.error}</div>}
            </div>

            <div>

                <label>Sex</label>

                <div>
                    <label>
                        <input
                            type="radio"
                            {...sex}
                            value="male"
                            checked={sex.value === 'male'}/> Male
                    </label>
                    <label>
                        <input
                            type="radio" {...sex}
                            value="female"
                            checked={sex.value === 'female'}/> Female
                    </label>
                </div>

                {sex.touched
                && sex.error
                && <div>{sex.error}</div>}

            </div>

            <button type="submit" >
                Submit
            </button>

        </form>);
    }
}

Form.propTypes = {
    fields: PropTypes.object.isRequired,
    handleSubmit: PropTypes.func.isRequired
};

/**
 * Map our form to redux-form
 *
 * asyncValidate : Validation in now async - The redux store will now have a section called userDetails which will store our form data
 *
 * fields - Tells redux-form the fields of our form and will spread its API across the objects (ready to be used in our form)
 *
 * valdate - Function to call when we need to validate.
 */
export default reduxForm({
    form: 'userDetails',
    fields,
    asyncValidate
})(Form);



{% endhighlight %}


## Conclusion

<code>yup</code> is an awesome, flexable and powerful tool to validate our data against a schema. With <code>redux-form</code> it seems like a nice tool chain that work well together.

[Free free to check the code on github.](https://github.com/boyney123/react-redux-form-yup-schema-example)


If you have any questions just [tweet me](https://twitter.com/boyney123), or leave a comment.
 




