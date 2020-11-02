# Aye Engineer !

You've been selected after a long training period to help POSOS develop its space program. We've watched all Space X launches, played KSP a lot and we've even built a LEGO Saturn V rocket. We're now ready to fly, trust me.

![POSOS experimental crew in orbit](statics/ksp.jpg)

## Your job

Beforehand, we need to develop some software to help us get our feet off the ground. The most important tool we need right now will help our lead engineer to find its way back to our office. He got lost when he went out buying some coffee and never came back. 

We're not sure if it was voluntary though, so let's try sending him a hint about our **offices geographic position** (which is `Latitude 48.8731039° North` and `Longitude 2.3128007° East`, about 87 meters above sea level).

## How to do that

Our scientists team has determined the most efficient way to provide our lead engineer with the most useful information to find his way back. We'll send him the current position of Galileo satellites in the sky above our office, so he can compute himself everything he needs by finding them over his head. We're not quite sure if it's what he needs but we're sure this information will help him. 

Hopefully, an API already exists that we'll do most of the job for us, you can find it there: [n2yo.com](https://www.n2yo.com/api/). Read the doc, you should find something that works. If you need an API key we can give one, or you can register and get one. Anyway, this shouldn't be hardcoded of course.

This API is nice but is not really usable as-is. So you'll need to build a lite interface:

1. First, your app should provide a nice button in the browser that writes back the satellites positions. If you're able to draw a nice looking-result, it would be nicer, but we don't expect you to have such high-grade skills. We don't want the whole page to reload each time you push the button, it's ugly and so '90-ish.

2. Second, our requests count per hour is limited. _Imagine all the people_, err... if all the employees got lost at the same time, if they'd all simutanously requested the service we'd be soon kicked off the API. We should keep a local copy of satellites data to be sure we don't kill the n2yo.com API.

3. Because the fastest satellite will be the first out of sight, please sort them by [orbital velocity](https://en.wikipedia.org/wiki/Orbital_speed) (assuming their orbit is circular around the Earth).

4. If you can also predict the visual passes of the satellites above our position for the next 2 days, it would greatly help our lost lead engineer.

## Output

### Software code

The first and main deliverable is your code. Please implement a software that fullfills our need, and respects the following constraints.

**Tech stack**
(:point_up: == mandatory, :woman_shrugging: == optional)

- :point_up: React. _If you want to use a framework_, the only one allowed would be [NextJS](https://nextjs.org/docs/)
- :point_up: css/scsss modules or styled components
- :point_up: Docker
- :woman_shrugging: Typescript backend

**Guidelines**
- it should be runnable as one or many Docker container. Provide any needed Docker and Docker Compose file you may find necessary. If your work is not Docker-compatible please justify and provide very detailed running documentation. A software that is not runnable by our 5 years old engineers will be eliminated.
- it should respect best security and software engineering practices

You should send us the link to a public `git` repository hosting your code.

### Documentation

Aside the "install & run" documentation, we'd like to know what drive your implementation and architecture decisions. Please tell us why you choose such language or pattern, how your solution compares to others, etc.
Please also answer the following questions:

1. How would you modify your project to handle horizontal scaling in such way we do not keep multiple copies of satellites data?
2. Imagine we do not track a dozen of satellites, but a million. How would you change your project to handle it?
3. What metrics should be produced by your software? What would they be useful for? Propose an implementation using Prometheus protocol.
4. Which assertion in the requirements and constraints is a scientific mistake, if any? This question won't give you any point.
