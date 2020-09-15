---
title: Dive into InversifyJS
date: 2020-09-12 23:53:23
tags:
- TypeScript
- InversifyJS
- Inversion of control
- Dependency injection
---

[InversifyJS](http://inversify.io/)

<Inversify的目的>

## Brief Introduction about Decorator

```ts
// 
declare type ClassDecorator = <TFunction extends Function>(target: TFunction) => TFunction | void;

declare type PropertyDecorator = (target: Object, propertyKey: string | symbol) => void;

declare type MethodDecorator = <T>(target: Object, propertyKey: string | symbol, descriptor: TypedPropertyDescriptor<T>) => TypedPropertyDescriptor<T> | void;

declare type ParameterDecorator = (target: Object, propertyKey: string | symbol, parameterIndex: number) => void;
```

## Using InversifyJS

1. Declare interface

> Our goal is to write code that adheres to the [dependency inversion principle](https://en.wikipedia.org/wiki/Dependency_inversion_principle). This means that we should "depend upon Abstractions and do not depend upon concretions". Let's start by declaring some interfaces (abstractions).

```ts
interface Warrior {
    fight(): string;
    sneak(): string;
}

interface Weapon {
    hit(): string;
}

interface ThrowableWeapon {
    throw(): string;
}
```

> InversifyJS need to use the type as identifiers at runtime. We use symbols as identifiers but you can also use classes and or string literals.

```ts
let TYPES = {
    Warrior: Symbol("Warrior"),
    Weapon: Symbol("Weapon"),
    ThrowableWeapon: Symbol("ThrowableWeapon")
};

export default TYPES;
```

2. Declaring classes and dependencies

```typescript
import { injectable, inject } from "inversify";
import "reflect-metadata";
import TYPES from "./types";

@injectable()
class Katana implements Weapon {
    public hit() {
        return "cut!";
    }
}

@injectable()
class Shuriken implements ThrowableWeapon {
    public throw() {
        return "hit!";
    }
}

@injectable()
class Ninja implements Warrior {

    private _katana: Weapon;
    private _shuriken: ThrowableWeapon;

    public constructor(
        @inject(TYPES.Weapon) katana: Weapon,
        @inject(TYPES.ThrowableWeapon) shuriken: ThrowableWeapon
    ) {
        this._katana = katana;
        this._shuriken = shuriken;
    }

    public fight() { return this._katana.hit(); };
    public sneak() { return this._shuriken.throw(); };

}

export { Ninja, Katana, Shuriken };
```





## What happend?



```ts
function injectable() {
  return function(target: any) {

    if (Reflect.hasOwnMetadata(METADATA_KEY.PARAM_TYPES, target)) {
      throw new Error(ERRORS_MSGS.DUPLICATED_INJECTABLE_DECORATOR);
    }

    const types = Reflect.getMetadata(METADATA_KEY.DESIGN_PARAM_TYPES, target) || [];
    Reflect.defineMetadata(METADATA_KEY.PARAM_TYPES, types, target);

    return target;
  };
}
```

injectable是一个装饰器工厂，从返回的装饰器可以看出这是一个类装饰器。 



```ts
function inject(serviceIdentifier: ServiceIdentifierOrFunc) {
  return function(target: any, targetKey: string, index?: number): void {
    if (serviceIdentifier === undefined) {
      throw new Error(UNDEFINED_INJECT_ANNOTATION(target.name));
    }

    const metadata = new Metadata(METADATA_KEY.INJECT_TAG, serviceIdentifier);

    if (typeof index === "number") {
      tagParameter(target, targetKey, index, metadata);
    } else {
      tagProperty(target, targetKey, metadata);
    }

  };
}
```





```ts
interface x {
    anotationTargetObject: {
        propertyName: {
            metadataKey: {
                metadata: {
                    // inversifyJS
                    [METADATA_KEY: string]: Metadata[];
                }
            }
        }
    }
}
// metadata keys of inversify
const enum METADATA_KEY {
    // used to store types to be injected
    PARAM_TYPES = "inversify:paramtypes",
    // used to access design time types
    DESIGN_PARAM_TYPES = "design:paramtypes",
    
    // The type of the binding at design time
    INJECT_TAG = "inject",
    // used to store constructor arguments tags
    TAGGED = "inversify:tagged",
    // used to store class properties tags
    TAGGED_PROP = "inversify:tagged_props",
    ...
}

interface Metadata {
    key: string | number | symbol;
    value: any;
    toString(): string;
}

type propertyName = string | symbol | undefined;
```



```
@inject(serviceIdentifier) 
          ||
          \/
{
  key: METADATA_KEY.INJECT_TAG,
  value: serviceIdentifier,
}: Metadata
```



> If you prefer it you can use property injection instead of constructor injection so you don't have to declare the class constructor:

```ts
@injectable()
class Ninja implements Warrior {
    @inject(TYPES.Weapon) private _katana: Weapon;
    @inject(TYPES.ThrowableWeapon) private _shuriken: ThrowableWeapon;
    public fight() { return this._katana.hit(); };
    public sneak() { return this._shuriken.throw(); };
}
```

3. Creating and configuring a Container

```ts
import { Container } from "inversify";
import TYPES from "./types";
import { Ninja, Katana, Shuriken } from "./entities";

var container = new Container();
container.bind<Warrior>(TYPES.Warrior).to(Ninja);
container.bind<Weapon>(TYPES.Weapon).to(Katana);
container.bind<ThrowableWeapon>(TYPES.ThrowableWeapon).to(Shuriken);

export default container;
```

4. Resolving dependencies

```ts
import container = from "./inversify.config";

var ninja = container.get<Warrior>(TYPES.Warrior);

expect(ninja.fight()).eql("cut!"); // true
expect(ninja.sneak()).eql("hit!"); // true
```

