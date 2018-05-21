---
title: 呼び出し元情報 (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 6f0cd4d9d8fc85cb15431ccb4c76eee14b3f67c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="caller-information-c"></a><span data-ttu-id="aab61-102">呼び出し元情報 (C#)</span><span class="sxs-lookup"><span data-stu-id="aab61-102">Caller Information (C#)</span></span>
<span data-ttu-id="aab61-103">呼び出し元情報の属性を使用すると、メソッドへの呼び出し元に関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="aab61-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="aab61-104">ソース コードのファイル パス、ソース コードの行番号、および呼び出し元のメンバー名を取得できます。</span><span class="sxs-lookup"><span data-stu-id="aab61-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="aab61-105">この情報は、トレース、デバッグ、および診断ツールの作成に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="aab61-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="aab61-106">この情報を取得するには、省略可能なパラメーターに適用される属性を使用します。各パラメーターには既定値があります。</span><span class="sxs-lookup"><span data-stu-id="aab61-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="aab61-107">次の表は、<xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 名前空間で定義されている呼び出し元情報の属性の一覧です。</span><span class="sxs-lookup"><span data-stu-id="aab61-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="aab61-108">属性</span><span class="sxs-lookup"><span data-stu-id="aab61-108">Attribute</span></span>|<span data-ttu-id="aab61-109">説明</span><span class="sxs-lookup"><span data-stu-id="aab61-109">Description</span></span>|<span data-ttu-id="aab61-110">型</span><span class="sxs-lookup"><span data-stu-id="aab61-110">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="aab61-111">呼び出し元を含むソース ファイルのフル パスです。</span><span class="sxs-lookup"><span data-stu-id="aab61-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="aab61-112">これは、コンパイル時のファイル パスです。</span><span class="sxs-lookup"><span data-stu-id="aab61-112">This is the file path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="aab61-113">メソッドが呼び出されたソース ファイルの行番号。</span><span class="sxs-lookup"><span data-stu-id="aab61-113">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="aab61-114">呼び出し元のメソッド名またはプロパティ名。</span><span class="sxs-lookup"><span data-stu-id="aab61-114">Method or property name of the caller.</span></span> <span data-ttu-id="aab61-115">後で説明する「[メンバー名](#MEMBERNAMES)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aab61-115">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="aab61-116">例</span><span class="sxs-lookup"><span data-stu-id="aab61-116">Example</span></span>  
 <span data-ttu-id="aab61-117">呼び出し元情報の属性を使用する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="aab61-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="aab61-118">`TraceMessage` メソッドを呼び出すたびに、呼び出し元情報は、省略可能なパラメーターの引数として設定されます。</span><span class="sxs-lookup"><span data-stu-id="aab61-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
```csharp  
public void DoProcessing()  
{  
    TraceMessage("Something happened.");  
}  
  
public void TraceMessage(string message,  
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",  
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",  
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)  
{  
    System.Diagnostics.Trace.WriteLine("message: " + message);  
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);  
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);  
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);  
}  
  
// Sample Output:  
//  message: Something happened.  
//  member name: DoProcessing  
//  source file path: c:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoCS\CallerInfoCS\Form1.cs  
//  source line number: 31  
```  
  
## <a name="remarks"></a><span data-ttu-id="aab61-119">コメント</span><span class="sxs-lookup"><span data-stu-id="aab61-119">Remarks</span></span>  
 <span data-ttu-id="aab61-120">省略可能な各パラメーターには、明示的な既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aab61-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="aab61-121">省略可能と指定されていないパラメーターには、呼び出し元情報の属性を適用できません。</span><span class="sxs-lookup"><span data-stu-id="aab61-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="aab61-122">呼び出し元情報の属性によってパラメーターが省略可能になるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="aab61-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="aab61-123">この属性は、引数を省略したときに渡される既定値に影響します。</span><span class="sxs-lookup"><span data-stu-id="aab61-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="aab61-124">呼び出し元情報の値は、コンパイル時に中間言語 (IL) 内にリテラルとして出力されます。</span><span class="sxs-lookup"><span data-stu-id="aab61-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="aab61-125">例外の <xref:System.Exception.StackTrace%2A> プロパティの結果とは異なり、難読化による影響は受けません。</span><span class="sxs-lookup"><span data-stu-id="aab61-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="aab61-126">省略可能な引数を明示的に指定して、呼び出し元情報を制御したり、非表示にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="aab61-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
###  <a name="MEMBERNAMES"></a><span data-ttu-id="aab61-127">メンバー名</span><span class="sxs-lookup"><span data-stu-id="aab61-127">Member Names</span></span>  
 <span data-ttu-id="aab61-128">`CallerMemberName` 属性を使用して、呼び出されたメソッドにメンバー名を `String` 引数として指定することを回避できます。</span><span class="sxs-lookup"><span data-stu-id="aab61-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="aab61-129">この方法を使用すると、**リファクタリングの名前の変更**で `String` 値が変更されないという問題が発生しなくなります。</span><span class="sxs-lookup"><span data-stu-id="aab61-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="aab61-130">この利点は、次のタスクで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="aab61-130">This benefit is especially useful for the following tasks:</span></span>  
  
-   <span data-ttu-id="aab61-131">トレース ルーチンと診断ルーチンの使用。</span><span class="sxs-lookup"><span data-stu-id="aab61-131">Using tracing and diagnostic routines.</span></span>  
  
-   <span data-ttu-id="aab61-132">データ バインディング時の <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスの実装。</span><span class="sxs-lookup"><span data-stu-id="aab61-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="aab61-133">このインターフェイスを使用すると、オブジェクトのプロパティが、プロパティが変更されたことをデータ バインド コントロールに通知できます。これによって、このコントロールは、更新された情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="aab61-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="aab61-134">`CallerMemberName` 属性がない場合は、リテラルとしてプロパティ名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aab61-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="aab61-135">次のグラフは、`CallerMemberName` 属性の使用時に返されるメンバー名を示します。</span><span class="sxs-lookup"><span data-stu-id="aab61-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="aab61-136">呼び出しは、次のものの中で発生します。</span><span class="sxs-lookup"><span data-stu-id="aab61-136">Calls occurs within</span></span>|<span data-ttu-id="aab61-137">メンバー名の結果</span><span class="sxs-lookup"><span data-stu-id="aab61-137">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="aab61-138">メソッド、プロパティ、またはイベント</span><span class="sxs-lookup"><span data-stu-id="aab61-138">Method, property, or event</span></span>|<span data-ttu-id="aab61-139">呼び出しが発生したメソッド、プロパティ、またはイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="aab61-139">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="aab61-140">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="aab61-140">Constructor</span></span>|<span data-ttu-id="aab61-141">文字列「.ctor」</span><span class="sxs-lookup"><span data-stu-id="aab61-141">The string ".ctor"</span></span>|  
|<span data-ttu-id="aab61-142">静的コンストラクター</span><span class="sxs-lookup"><span data-stu-id="aab61-142">Static constructor</span></span>|<span data-ttu-id="aab61-143">文字列「.cctor」</span><span class="sxs-lookup"><span data-stu-id="aab61-143">The string ".cctor"</span></span>|  
|<span data-ttu-id="aab61-144">デストラクターです。</span><span class="sxs-lookup"><span data-stu-id="aab61-144">Destructor</span></span>|<span data-ttu-id="aab61-145">文字列「Finalize」</span><span class="sxs-lookup"><span data-stu-id="aab61-145">The string "Finalize"</span></span>|  
|<span data-ttu-id="aab61-146">ユーザー定義の演算子または変換</span><span class="sxs-lookup"><span data-stu-id="aab61-146">User-defined operators or conversions</span></span>|<span data-ttu-id="aab61-147">生成されたメンバー名 (「op_Addition」など)。</span><span class="sxs-lookup"><span data-stu-id="aab61-147">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="aab61-148">Attribute コンストラクター</span><span class="sxs-lookup"><span data-stu-id="aab61-148">Attribute constructor</span></span>|<span data-ttu-id="aab61-149">属性が適用されるメンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="aab61-149">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="aab61-150">属性がメンバー内の要素 (パラメーター、戻り値、ジェネリック型パラメーターなど) である場合、この結果は、その要素に関連付けられているメンバーの名前になります。</span><span class="sxs-lookup"><span data-stu-id="aab61-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="aab61-151">含んでいないメンバー (型に適用されているアセンブリ レベルや属性など)</span><span class="sxs-lookup"><span data-stu-id="aab61-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="aab61-152">省略可能なパラメーターの既定値。</span><span class="sxs-lookup"><span data-stu-id="aab61-152">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aab61-153">参照</span><span class="sxs-lookup"><span data-stu-id="aab61-153">See Also</span></span>  
 [<span data-ttu-id="aab61-154">属性 (C#)</span><span class="sxs-lookup"><span data-stu-id="aab61-154">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="aab61-155">共通属性 (C#)</span><span class="sxs-lookup"><span data-stu-id="aab61-155">Common Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
 [<span data-ttu-id="aab61-156">名前付き引数と省略可能な引数</span><span class="sxs-lookup"><span data-stu-id="aab61-156">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [<span data-ttu-id="aab61-157">プログラミングの概念 (C#)</span><span class="sxs-lookup"><span data-stu-id="aab61-157">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)
