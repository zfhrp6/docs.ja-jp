---
title: "呼び出し元情報 (f#)"
description: "呼び出し元情報引数属性を使用して、メソッドから呼び出し元情報を取得する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 04/25/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 533d2f0429ddb31e6d1dd7efca2f0760069a2945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="caller-information"></a><span data-ttu-id="a556a-104">呼び出し元情報</span><span class="sxs-lookup"><span data-stu-id="a556a-104">Caller information</span></span>

<span data-ttu-id="a556a-105">呼び出し元情報の属性を使用すると、メソッドへの呼び出し元に関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="a556a-105">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="a556a-106">ソース コードのファイル パス、ソース コードの行番号、および呼び出し元のメンバー名を取得できます。</span><span class="sxs-lookup"><span data-stu-id="a556a-106">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="a556a-107">この情報は、トレース、デバッグ、および診断ツールの作成に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a556a-107">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="a556a-108">この情報を取得するには、省略可能なパラメーターに適用される属性を使用します。各パラメーターには既定値があります。</span><span class="sxs-lookup"><span data-stu-id="a556a-108">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="a556a-109">次の表に、呼び出し元情報属性で定義されている、 [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices)名前空間。</span><span class="sxs-lookup"><span data-stu-id="a556a-109">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="a556a-110">属性</span><span class="sxs-lookup"><span data-stu-id="a556a-110">Attribute</span></span>|<span data-ttu-id="a556a-111">説明</span><span class="sxs-lookup"><span data-stu-id="a556a-111">Description</span></span>|<span data-ttu-id="a556a-112">型</span><span class="sxs-lookup"><span data-stu-id="a556a-112">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="a556a-113">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="a556a-113">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="a556a-114">呼び出し元を含むソース ファイルのフル パスです。</span><span class="sxs-lookup"><span data-stu-id="a556a-114">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="a556a-115">これは、コンパイル時のファイル パスです。</span><span class="sxs-lookup"><span data-stu-id="a556a-115">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="a556a-116">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="a556a-116">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="a556a-117">メソッドが呼び出されたソース ファイルの行番号。</span><span class="sxs-lookup"><span data-stu-id="a556a-117">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="a556a-118">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="a556a-118">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="a556a-119">呼び出し元のメソッド名またはプロパティ名。</span><span class="sxs-lookup"><span data-stu-id="a556a-119">Method or property name of the caller.</span></span> <span data-ttu-id="a556a-120">このトピックの「メンバー名を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a556a-120">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="a556a-121">例</span><span class="sxs-lookup"><span data-stu-id="a556a-121">Example</span></span>

<span data-ttu-id="a556a-122">次の例では、これらの属性を呼び出し元のトレースを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a556a-122">The following example shows how you might use these attributes to trace a caller.</span></span>

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices

type Tracer() =
    member __.DoTrace(msg: string,
                      [<CallerMemberName>] ?memberName: string,
                      [<CallerFilePath>] ?path: string
                      [<CallerLineNumber>] ?line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        match (memberName, path, line) with
        | Some m, Some p, Some l ->
            Trace.WriteLine(sprintf "Member name: %s" m)
            Trace.WriteLine(sprintf "Source file path: %s" p)
            Trace.WriteLine(sprintf "Source line number: %d" l)
        | _,_,_ -> ()
```

## <a name="remarks"></a><span data-ttu-id="a556a-123">コメント</span><span class="sxs-lookup"><span data-stu-id="a556a-123">Remarks</span></span>

<span data-ttu-id="a556a-124">呼び出し元情報属性は、省略可能なパラメーターにのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="a556a-124">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="a556a-125">省略可能な各パラメーターの明示的な値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a556a-125">You must supply an explicit value for each optional parameter.</span></span> <span data-ttu-id="a556a-126">呼び出し元情報属性では、呼び出し元情報属性で修飾された各省略可能なパラメーターの適切な値の書き込みにコンパイラがあります。</span><span class="sxs-lookup"><span data-stu-id="a556a-126">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="a556a-127">呼び出し元情報の値は、コンパイル時に中間言語 (IL) 内にリテラルとして出力されます。</span><span class="sxs-lookup"><span data-stu-id="a556a-127">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="a556a-128">結果とは異なり、 [StackTrace](/dotnet/api/system.diagnostics.stacktrace)難読化によるプロパティの例外、結果の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="a556a-128">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="a556a-129">省略可能な引数を明示的に指定して、呼び出し元情報を制御したり、非表示にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="a556a-129">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="a556a-130">メンバー名</span><span class="sxs-lookup"><span data-stu-id="a556a-130">Member names</span></span>

<span data-ttu-id="a556a-131">使用することができます、 [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)属性とメンバーの名前を指定しない場合に、`String`呼び出されたメソッドに渡す引数。</span><span class="sxs-lookup"><span data-stu-id="a556a-131">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="a556a-132">この手法を使用すると、名前の変更リファクタリング変更されない問題を回避する、`String`値。</span><span class="sxs-lookup"><span data-stu-id="a556a-132">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="a556a-133">この利点は、次のタスクで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a556a-133">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="a556a-134">トレース ルーチンと診断ルーチンの使用。</span><span class="sxs-lookup"><span data-stu-id="a556a-134">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="a556a-135">実装する、 [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged)インターフェイスのデータをバインドするときにします。</span><span class="sxs-lookup"><span data-stu-id="a556a-135">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="a556a-136">このインターフェイスを使用すると、オブジェクトのプロパティが、プロパティが変更されたことをデータ バインド コントロールに通知できます。これによって、このコントロールは、更新された情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="a556a-136">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="a556a-137">なし、 [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)属性、リテラルとしてプロパティ名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a556a-137">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="a556a-138">次の表は、メンバー CallerMemberName 属性を使用するときに返される名を示します。</span><span class="sxs-lookup"><span data-stu-id="a556a-138">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="a556a-139">呼び出しは、次のものの中で発生します。</span><span class="sxs-lookup"><span data-stu-id="a556a-139">Calls occurs within</span></span>|<span data-ttu-id="a556a-140">メンバー名の結果</span><span class="sxs-lookup"><span data-stu-id="a556a-140">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="a556a-141">メソッド、プロパティ、またはイベント</span><span class="sxs-lookup"><span data-stu-id="a556a-141">Method, property, or event</span></span>|<span data-ttu-id="a556a-142">呼び出しが発生したメソッド、プロパティ、またはイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="a556a-142">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="a556a-143">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="a556a-143">Constructor</span></span>|<span data-ttu-id="a556a-144">文字列「.ctor」</span><span class="sxs-lookup"><span data-stu-id="a556a-144">The string ".ctor"</span></span>|
|<span data-ttu-id="a556a-145">静的コンストラクター</span><span class="sxs-lookup"><span data-stu-id="a556a-145">Static constructor</span></span>|<span data-ttu-id="a556a-146">文字列「.cctor」</span><span class="sxs-lookup"><span data-stu-id="a556a-146">The string ".cctor"</span></span>|
|<span data-ttu-id="a556a-147">デストラクターです。</span><span class="sxs-lookup"><span data-stu-id="a556a-147">Destructor</span></span>|<span data-ttu-id="a556a-148">文字列「Finalize」</span><span class="sxs-lookup"><span data-stu-id="a556a-148">The string "Finalize"</span></span>|
|<span data-ttu-id="a556a-149">ユーザー定義の演算子または変換</span><span class="sxs-lookup"><span data-stu-id="a556a-149">User-defined operators or conversions</span></span>|<span data-ttu-id="a556a-150">生成されたメンバー名 (「op_Addition」など)。</span><span class="sxs-lookup"><span data-stu-id="a556a-150">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="a556a-151">Attribute コンストラクター</span><span class="sxs-lookup"><span data-stu-id="a556a-151">Attribute constructor</span></span>|<span data-ttu-id="a556a-152">属性が適用されるメンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="a556a-152">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="a556a-153">属性がメンバー内の要素 (パラメーター、戻り値、ジェネリック型パラメーターなど) である場合、この結果は、その要素に関連付けられているメンバーの名前になります。</span><span class="sxs-lookup"><span data-stu-id="a556a-153">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="a556a-154">含んでいないメンバー (型に適用されているアセンブリ レベルや属性など)</span><span class="sxs-lookup"><span data-stu-id="a556a-154">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="a556a-155">省略可能なパラメーターの既定値。</span><span class="sxs-lookup"><span data-stu-id="a556a-155">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a556a-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="a556a-156">See also</span></span>
 [<span data-ttu-id="a556a-157">属性</span><span class="sxs-lookup"><span data-stu-id="a556a-157">Attributes</span></span>](attributes.md)  
 [<span data-ttu-id="a556a-158">名前付き引数</span><span class="sxs-lookup"><span data-stu-id="a556a-158">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)  
 [<span data-ttu-id="a556a-159">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="a556a-159">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)  
