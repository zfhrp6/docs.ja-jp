---
title: 呼び出し元情報 (f#)
description: 呼び出し元情報引数属性を使用して、メソッドから呼び出し元情報を取得する方法について説明します。
author: cartermp
ms.author: phcart
ms.date: 04/25/2017
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 840c6c6308c55fe2a2dbefd52b159a32fb92f787
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="caller-information"></a><span data-ttu-id="0da17-103">呼び出し元情報</span><span class="sxs-lookup"><span data-stu-id="0da17-103">Caller information</span></span>

<span data-ttu-id="0da17-104">呼び出し元情報の属性を使用すると、メソッドへの呼び出し元に関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="0da17-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="0da17-105">ソース コードのファイル パス、ソース コードの行番号、および呼び出し元のメンバー名を取得できます。</span><span class="sxs-lookup"><span data-stu-id="0da17-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="0da17-106">この情報は、トレース、デバッグ、および診断ツールの作成に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0da17-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="0da17-107">この情報を取得するには、省略可能なパラメーターに適用される属性を使用します。各パラメーターには既定値があります。</span><span class="sxs-lookup"><span data-stu-id="0da17-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="0da17-108">次の表に、呼び出し元情報属性で定義されている、 [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices)名前空間。</span><span class="sxs-lookup"><span data-stu-id="0da17-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="0da17-109">属性</span><span class="sxs-lookup"><span data-stu-id="0da17-109">Attribute</span></span>|<span data-ttu-id="0da17-110">説明</span><span class="sxs-lookup"><span data-stu-id="0da17-110">Description</span></span>|<span data-ttu-id="0da17-111">型</span><span class="sxs-lookup"><span data-stu-id="0da17-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="0da17-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="0da17-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="0da17-113">呼び出し元を含むソース ファイルのフル パスです。</span><span class="sxs-lookup"><span data-stu-id="0da17-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="0da17-114">これは、コンパイル時のファイル パスです。</span><span class="sxs-lookup"><span data-stu-id="0da17-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="0da17-115">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="0da17-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="0da17-116">メソッドが呼び出されたソース ファイルの行番号。</span><span class="sxs-lookup"><span data-stu-id="0da17-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="0da17-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="0da17-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="0da17-118">呼び出し元のメソッド名またはプロパティ名。</span><span class="sxs-lookup"><span data-stu-id="0da17-118">Method or property name of the caller.</span></span> <span data-ttu-id="0da17-119">このトピックの「メンバー名を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0da17-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="0da17-120">例</span><span class="sxs-lookup"><span data-stu-id="0da17-120">Example</span></span>

<span data-ttu-id="0da17-121">次の例では、これらの属性を呼び出し元のトレースを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0da17-121">The following example shows how you might use these attributes to trace a caller.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="0da17-122">コメント</span><span class="sxs-lookup"><span data-stu-id="0da17-122">Remarks</span></span>

<span data-ttu-id="0da17-123">呼び出し元情報属性は、省略可能なパラメーターにのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="0da17-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="0da17-124">省略可能な各パラメーターの明示的な値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0da17-124">You must supply an explicit value for each optional parameter.</span></span> <span data-ttu-id="0da17-125">呼び出し元情報属性では、呼び出し元情報属性で修飾された各省略可能なパラメーターの適切な値の書き込みにコンパイラがあります。</span><span class="sxs-lookup"><span data-stu-id="0da17-125">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="0da17-126">呼び出し元情報の値は、コンパイル時に中間言語 (IL) 内にリテラルとして出力されます。</span><span class="sxs-lookup"><span data-stu-id="0da17-126">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="0da17-127">結果とは異なり、 [StackTrace](/dotnet/api/system.diagnostics.stacktrace)難読化によるプロパティの例外、結果の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="0da17-127">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="0da17-128">省略可能な引数を明示的に指定して、呼び出し元情報を制御したり、非表示にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="0da17-128">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="0da17-129">メンバー名</span><span class="sxs-lookup"><span data-stu-id="0da17-129">Member names</span></span>

<span data-ttu-id="0da17-130">使用することができます、 [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)属性とメンバーの名前を指定しない場合に、`String`呼び出されたメソッドに渡す引数。</span><span class="sxs-lookup"><span data-stu-id="0da17-130">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="0da17-131">この手法を使用すると、名前の変更リファクタリング変更されない問題を回避する、`String`値。</span><span class="sxs-lookup"><span data-stu-id="0da17-131">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="0da17-132">この利点は、次のタスクで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0da17-132">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="0da17-133">トレース ルーチンと診断ルーチンの使用。</span><span class="sxs-lookup"><span data-stu-id="0da17-133">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="0da17-134">実装する、 [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged)インターフェイスのデータをバインドするときにします。</span><span class="sxs-lookup"><span data-stu-id="0da17-134">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="0da17-135">このインターフェイスを使用すると、オブジェクトのプロパティが、プロパティが変更されたことをデータ バインド コントロールに通知できます。これによって、このコントロールは、更新された情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="0da17-135">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="0da17-136">なし、 [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)属性、リテラルとしてプロパティ名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0da17-136">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="0da17-137">次の表は、メンバー CallerMemberName 属性を使用するときに返される名を示します。</span><span class="sxs-lookup"><span data-stu-id="0da17-137">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="0da17-138">呼び出しは、次のものの中で発生します。</span><span class="sxs-lookup"><span data-stu-id="0da17-138">Calls occurs within</span></span>|<span data-ttu-id="0da17-139">メンバー名の結果</span><span class="sxs-lookup"><span data-stu-id="0da17-139">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="0da17-140">メソッド、プロパティ、またはイベント</span><span class="sxs-lookup"><span data-stu-id="0da17-140">Method, property, or event</span></span>|<span data-ttu-id="0da17-141">呼び出しが発生したメソッド、プロパティ、またはイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="0da17-141">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="0da17-142">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="0da17-142">Constructor</span></span>|<span data-ttu-id="0da17-143">文字列「.ctor」</span><span class="sxs-lookup"><span data-stu-id="0da17-143">The string ".ctor"</span></span>|
|<span data-ttu-id="0da17-144">静的コンストラクター</span><span class="sxs-lookup"><span data-stu-id="0da17-144">Static constructor</span></span>|<span data-ttu-id="0da17-145">文字列「.cctor」</span><span class="sxs-lookup"><span data-stu-id="0da17-145">The string ".cctor"</span></span>|
|<span data-ttu-id="0da17-146">デストラクターです。</span><span class="sxs-lookup"><span data-stu-id="0da17-146">Destructor</span></span>|<span data-ttu-id="0da17-147">文字列「Finalize」</span><span class="sxs-lookup"><span data-stu-id="0da17-147">The string "Finalize"</span></span>|
|<span data-ttu-id="0da17-148">ユーザー定義の演算子または変換</span><span class="sxs-lookup"><span data-stu-id="0da17-148">User-defined operators or conversions</span></span>|<span data-ttu-id="0da17-149">生成されたメンバー名 (「op_Addition」など)。</span><span class="sxs-lookup"><span data-stu-id="0da17-149">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="0da17-150">Attribute コンストラクター</span><span class="sxs-lookup"><span data-stu-id="0da17-150">Attribute constructor</span></span>|<span data-ttu-id="0da17-151">属性が適用されるメンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="0da17-151">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="0da17-152">属性がメンバー内の要素 (パラメーター、戻り値、ジェネリック型パラメーターなど) である場合、この結果は、その要素に関連付けられているメンバーの名前になります。</span><span class="sxs-lookup"><span data-stu-id="0da17-152">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="0da17-153">含んでいないメンバー (型に適用されているアセンブリ レベルや属性など)</span><span class="sxs-lookup"><span data-stu-id="0da17-153">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="0da17-154">省略可能なパラメーターの既定値。</span><span class="sxs-lookup"><span data-stu-id="0da17-154">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="0da17-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="0da17-155">See also</span></span>
 [<span data-ttu-id="0da17-156">属性</span><span class="sxs-lookup"><span data-stu-id="0da17-156">Attributes</span></span>](attributes.md)  
 [<span data-ttu-id="0da17-157">名前付き引数</span><span class="sxs-lookup"><span data-stu-id="0da17-157">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)  
 [<span data-ttu-id="0da17-158">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="0da17-158">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)  
