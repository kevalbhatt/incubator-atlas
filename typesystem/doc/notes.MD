# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements.  See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership.  The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

## Call with Harish on the initial typesystem naming conventions and intentions

### Structs are like C structs - they don't have an identity
- no independent lifecycle
- like a bag of properties
- like in hive, also

### Classes are classes
- like any OO class
- have identity
- can have inheritence
- can contain structs
- don't necessarily need to use a struct inside the class to define props
- can also define props using AttributeDefinition using the basic data types
- classes are immutable once created

### On search interface:
- can search for all instances of a class
- classes could become tables in a relational system, for instance
	- also databases, columns, etc.

### Traits is similar to scala - traits more like decorators (?)
- traits get applied to instances - not classes
	- this satisfies the classification mechanism (ish)
- can have a class instance have any number of traits
- e.g. security clearance - any Person class could have it; so we add it as a mixin to the Person class
	- security clearance trait has a level attribute
	- traits are labels
	- each label can have its own attribute
- reason for doing this is:
	- modeled security clearance trait
	- want to prescribe it to other things, too
	- can now search for anything that has security clearance level = 1, for instance

### On Instances:
- class, trait, struct all have bags of attributes
- can get name of type associated with attribute
- can get or set the attribute in that bag for each instance

### On Classification:
- create column as a class
- create a trait to classify as "PHI"
- would create the instance of the column with the PHI trait
- apply traits to instances
- CAN'T apply traits to class

### Other useful information

HierarchicalClassType - base type for ClassType and TraitType
Instances created from Definitions

Every instance is referenceable - i.e. something can point to it in the graph db
MetadataService may not be used longterm - it is currently used for bootstrapping the repo & type system

Id class - represents the Id of an instance

When the web service receives an object graph, the ObjectGraphWalker is used to update things
	- DiscoverInstances is used to discover the instances in the object graph received by the web service
	
MapIds assigns new ids to the discovered instances in the object graph

Anything under the storage package is not part of the public interface