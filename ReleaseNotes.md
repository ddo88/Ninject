Version 4.0
----------------
- Add support for NETSTANDARD1.3 and NETSTANDARD1.5
- Removed support for .NET 3.5
- Removed support for Windows Phone 7.x
- Removed support for .NET compact framework
- Removed support for Mono < 3.x
- Removed support for Silverlight < 5

Version 3.2
---------------
- Add: bool IRequest.ForceUnique: In case there is an uncoditional and a conditional binding, return the conditional one. In case there are multiple unconditional or conditional bindings, throw an exception.
- Add: IResolutionRoot.TryGetAndThrowOnInvalidBinding<T> (extension method): Returns null if there is no binding, but throws ActivationException in case there is a binding which could not be activated.
- Add: TypeMatchingConstructorArgument introduced.
- Add: ToConstructor() can now accept results from methods as argument e.g. ToConstructor(_ => new Foo(this.GetBar())
- Add: WhenNoAncestorMatches, WhenAnyAncestorMatches and WhenNoAncestorNamed When overloads
- Add: WeakConstructorArgument and WeakPropertyValue that keep a weak reference to the value only so that Ninject has no reference on them when caching the created instance.
- Add: Overloads for WhenInjectedInto and WhenInjectedExactlyInto that take multiple types to support multiple allowed parents.
- Change: Added WhenAnyAncestorNamed and marked mispelled WhenAnyAnchestorNamed as obsolete 
- Change: Release method was moved from IKernel to the IResolutionRoot interface 
- Bugfix: Private properties of base class were not checked for existence of setter and Inject attribute
- Bugfix: When an object that is the scope of another object is released an Exception was thrown. 

Version 3.0.1
---------------
- Add: The default scope can be changed in the NinjectSettings using 
- Change: Open generics can now be passed to WhenInjectedInto
- Bugfix: Fixed race condition in the GarbageCollectionCachePruner

Version 3.0.0 (final)
---------------
- Change: The constructor scorer ignores implicit bindings
- Change: The constructor scorer ignores self bindings

Version 3.0.0-rc3
---------------
- Added: Support for default parameters. If not explicit binding exists for a dependency but there is default value defined it is used instead.
- Added: Support to define the constructor and constructor arguments using ToConstructor "to" overload
- Added: WhenInjectedExactlyInto When overload: Matches only if the target is exactly the specified type. This was the behavior of WhenInjectedInto in Ninject 2.2.
- Added: WhenAnyAnchestorNamed. Matches if any of the anchestor bindings is named with the specified name.
- Added default binding for IResolutionRoot that returns the kernel.
- Added: Open generic bindings can be overriden by closed generics for specific types.
- Added: Support for extensions that they can define bindings that return the same instance for different interfaces (interface segregation principle).
- Added: Generic Overloads for OnActivation and OnDeactivation that can be used to cast the implementation type. 
- Added: Bind<T1,T2, ...>() to define multiple interfaces for one service.
- Added: Rebind<T1,T2, ...>() to define multiple interfaces for one service.
- Added: Support to inject constructor arguments to deeper levels using new ConstructorArgument("name", value, true)

- Changed: WhenInjectedInto matches also if the target derives from the specified type.
- Changed: ToConstant bindings are in singleton scope by default
- Changed: Separate project for medium trust environments.
- Changed: Open generic bindings can be overwritten by closed generic bindings
- Changed: Ninject modules have a new method VerifyRequiredModulesAreLoaded to check if their dependencies are loaded.
- Changed: If several constructors have the same score an ActivationExcpetion is thrown.

- Removed: No web builds. All builds are have no reference to web anymore

- Bugfix, Breaking change: Get all will now return all bindings and not skip unconditional ones anymore in case there is a conditional one. This is the same behavior as the version 2.0.1 and bevore had. 
- Bugfix: Fixed that the CF and SL version of the activation cache did not properly remove the weak references
- Bugfix (for CF): The CF version threw an exception when a class had a generic method on a base class. This bugfix has the side effect that the Inject attribute cannot be defined on base methods anymore. It has to be defined on the overriden method! 
- Bugfix. The constructor scorer accepts default values
- Bugfix: The constructor scorer accepts self bindings


Version 2.2.1.0
---------------
- Bug Fix: For classes that have several virtual indexers and at least one of them overridden an ambiguous match exception was thrown when they were injected.
