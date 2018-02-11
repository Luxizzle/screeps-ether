# Ether

Ether is an AI im writing for Screeps.

# Usage

Create file `.env` in root and edit it:
```
TOKEN=SCREEPS_TOKEN
```

Build and upload: `npm run build` or `gulp`

# Todo

- Make carrier able to construct. 
	
	carry-only creeps are useless on later levels

- role.defender
- role tiers
	
	In preperation for future we need to be able to build tiers from cheap too expensive.

- towers
- Auto path building

	To improve efficiency in swampy areas we want to construct pathways from important objects to resources

- Caching basic stuff like my own creeps in a room.

	At this point we've been doing stuff like Room.find, which can be cpu expensive on every call. A simple loop over all the rooms with some basic stuff like Room.myScreeps would simplify and lower cpu cost

- Cache paths to resources
	- In combinations with the path building

- Create concept for a manager that will manage everything from construction to energy sharing
	- One core manager under `Game.manager`
	- Has a memory slot under `Memory.manager`
	- Has sub modules based on the type of management
		- These have a memory slot under `Memory.manager.modules[module]`

- Body sorting

	To make creeps more tougher, we should create a way to sort body parts on importance and logic.
	If a creep is unable to do its job due to lost body parts, kill it.

- Memory optimization

	Im not sure how memory is managed but from what i understand from the docs is that every time you call from Memory it gets parsed from and to json, which is cpu expensive.

	To fix this issue there will be memory proxy which acts in place of the original memory. At the starting tick we will initialize this proxy and at the end we will save it.

	This will only create 1 get and 1 set request, thus way less json parsing and stringifying.

- Move creep loop to Room.creeps instead of Game.creeps

	In combination with the caching. And moving creeps to their rooms will allow us to get insight into cpu usage per room

- Implement custom NBA pathfinding with caching and area waypoints