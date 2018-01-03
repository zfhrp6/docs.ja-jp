---
title: "結果 (f#)"
description: "エラー トレラント コードを作成するのに役立つ、f# '結果' の型を使用する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a15b5cf1-9055-4481-918c-4c8a051b5829
ms.openlocfilehash: e6535b11464f5de0515c05e6678f6328f48a676a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="results"></a>結果

4.1 以降では f# である、`Result<'T,'TFailure>`組み込むことのできるエラー トレラント コードを記述するために使用できる型です。

## <a name="syntax"></a>構文

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> = 
    | Ok of ResultValue:'T 
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a>コメント

結果の型は、[構造体の判別共用体](discriminated-unions.md#struct-discriminated-unions)、f# 4.1 で導入された他の機能であります。  ここの構造の等値セマンティクスが適用されます。

`Result` Monadic エラーの処理では、多くの場合と呼ばれる型が使用される通常[連続的指向プログラミング](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html)f# のコミュニティ内です。  次の単純な例では、この方法を示します。

```fsharp
// Define a simple type which has fields that can be validated
type Request = 
    { Name: string
      Email: string }

// Define some logic for what defines a valid name.
//
// Generates a Result which is an Ok if the name validates;
// otherwise, it generates a Result which is an Error.
let validateName req =
    match req.Name with
    | null -> Error "No name found."
    | "" -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | "" -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> Ok req

let validateRequest reqResult =
    reqResult 
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() = 
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (Ok req1)
    match res1 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (Ok req2)
    match res2 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

非常に簡単をすべて返すことを強制した場合は、さまざまな検証機能を連結することがわかります、`Result`です。  これによりを細かくする必要があるとコンポーザブルとしては次のような機能に分割できます。  付加価値もあります*強制*の使用[パターンに一致する](pattern-matching.md)検証のラウンドの最後に、プログラムの正確性を適用する交替でします。

## <a name="see-also"></a>参照

[判別共用体](discriminated-unions.md)

[パターン一致](pattern-matching.md)
