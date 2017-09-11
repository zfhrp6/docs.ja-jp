---
title: "呼び出し元情報 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d9a028474a3bb7ae020f466d4dfe51608c43ab07
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="caller-information-visual-basic"></a><span data-ttu-id="55b21-102">呼び出し元情報 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55b21-102">Caller Information (Visual Basic)</span></span>
<span data-ttu-id="55b21-103">呼び出し元情報の属性を使用すると、メソッドへの呼び出し元に関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="55b21-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="55b21-104">ソース コードのファイル パス、ソース コードの行番号、および呼び出し元のメンバー名を取得できます。</span><span class="sxs-lookup"><span data-stu-id="55b21-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="55b21-105">この情報は、トレース、デバッグ、および診断ツールの作成に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="55b21-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="55b21-106">この情報を取得するには、省略可能なパラメーターに適用される属性を使用します。各パラメーターには既定値があります。</span><span class="sxs-lookup"><span data-stu-id="55b21-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="55b21-107">次の表に、呼び出し元情報属性で定義されている、<xref:System.Runtime.CompilerServices?displayProperty=fullName>名前空間:</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="55b21-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="55b21-108">属性</span><span class="sxs-lookup"><span data-stu-id="55b21-108">Attribute</span></span>|<span data-ttu-id="55b21-109">説明</span><span class="sxs-lookup"><span data-stu-id="55b21-109">Description</span></span>|<span data-ttu-id="55b21-110">型</span><span class="sxs-lookup"><span data-stu-id="55b21-110">Type</span></span>|  
|---|---|---|  
|<span data-ttu-id="55b21-111"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span><span class="sxs-lookup"><span data-stu-id="55b21-111"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span></span>|<span data-ttu-id="55b21-112">呼び出し元を含むソース ファイルのフル パスです。</span><span class="sxs-lookup"><span data-stu-id="55b21-112">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="55b21-113">これは、コンパイル時のファイル パスです。</span><span class="sxs-lookup"><span data-stu-id="55b21-113">This is the file path at compile time.</span></span>|`String`|  
|<span data-ttu-id="55b21-114"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span><span class="sxs-lookup"><span data-stu-id="55b21-114"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span></span>|<span data-ttu-id="55b21-115">メソッドが呼び出されたソース ファイルの行番号。</span><span class="sxs-lookup"><span data-stu-id="55b21-115">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<span data-ttu-id="55b21-116"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span><span class="sxs-lookup"><span data-stu-id="55b21-116"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span></span>|<span data-ttu-id="55b21-117">呼び出し元のメソッド名またはプロパティ名。</span><span class="sxs-lookup"><span data-stu-id="55b21-117">Method or property name of the caller.</span></span> <span data-ttu-id="55b21-118">参照してください[メンバー名](#MEMBERNAMES)このトピックで後述します。</span><span class="sxs-lookup"><span data-stu-id="55b21-118">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="55b21-119">例</span><span class="sxs-lookup"><span data-stu-id="55b21-119">Example</span></span>  
 <span data-ttu-id="55b21-120">呼び出し元情報の属性を使用する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="55b21-120">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="55b21-121">`TraceMessage` メソッドを呼び出すたびに、呼び出し元情報は、省略可能なパラメーターの引数として設定されます。</span><span class="sxs-lookup"><span data-stu-id="55b21-121">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a><span data-ttu-id="55b21-122">解説</span><span class="sxs-lookup"><span data-stu-id="55b21-122">Remarks</span></span>  
 <span data-ttu-id="55b21-123">省略可能な各パラメーターには、明示的な既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55b21-123">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="55b21-124">省略可能と指定されていないパラメーターには、呼び出し元情報の属性を適用できません。</span><span class="sxs-lookup"><span data-stu-id="55b21-124">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="55b21-125">呼び出し元情報の属性によってパラメーターが省略可能になるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="55b21-125">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="55b21-126">この属性は、引数を省略したときに渡される既定値に影響します。</span><span class="sxs-lookup"><span data-stu-id="55b21-126">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="55b21-127">呼び出し元情報の値は、コンパイル時に中間言語 (IL) 内にリテラルとして出力されます。</span><span class="sxs-lookup"><span data-stu-id="55b21-127">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="55b21-128">結果とは異なり、<xref:System.Exception.StackTrace%2A>難読化によるプロパティは、結果の例外の影響を受けません</xref:System.Exception.StackTrace%2A>。</span><span class="sxs-lookup"><span data-stu-id="55b21-128">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="55b21-129">省略可能な引数を明示的に指定して、呼び出し元情報を制御したり、非表示にしたりできます。</span><span class="sxs-lookup"><span data-stu-id="55b21-129">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
###  <span data-ttu-id="55b21-130"><a name="MEMBERNAMES"></a>メンバー名</span><span class="sxs-lookup"><span data-stu-id="55b21-130"><a name="MEMBERNAMES"></a> Member Names</span></span>  
 <span data-ttu-id="55b21-131">`CallerMemberName` 属性を使用して、呼び出されたメソッドにメンバー名を `String` 引数として指定することを回避できます。</span><span class="sxs-lookup"><span data-stu-id="55b21-131">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="55b21-132">この手法を使用すると、問題を回避するを**名前の変更リファクタリング**変更されない、`String`値。</span><span class="sxs-lookup"><span data-stu-id="55b21-132">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="55b21-133">この利点は、次のタスクで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="55b21-133">This benefit is especially useful for the following tasks:</span></span>  
  
-   <span data-ttu-id="55b21-134">トレース ルーチンと診断ルーチンの使用。</span><span class="sxs-lookup"><span data-stu-id="55b21-134">Using tracing and diagnostic routines.</span></span>  
  
-   <span data-ttu-id="55b21-135">実装する、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスのデータをバインドする場合</xref:System.ComponentModel.INotifyPropertyChanged>。</span><span class="sxs-lookup"><span data-stu-id="55b21-135">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="55b21-136">このインターフェイスを使用すると、オブジェクトのプロパティが、プロパティが変更されたことをデータ バインド コントロールに通知できます。これによって、このコントロールは、更新された情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="55b21-136">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="55b21-137">`CallerMemberName` 属性がない場合は、リテラルとしてプロパティ名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55b21-137">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="55b21-138">次のグラフは、`CallerMemberName` 属性の使用時に返されるメンバー名を示します。</span><span class="sxs-lookup"><span data-stu-id="55b21-138">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="55b21-139">呼び出しは、次のものの中で発生します。</span><span class="sxs-lookup"><span data-stu-id="55b21-139">Calls occurs within</span></span>|<span data-ttu-id="55b21-140">メンバー名の結果</span><span class="sxs-lookup"><span data-stu-id="55b21-140">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="55b21-141">メソッド、プロパティ、またはイベント</span><span class="sxs-lookup"><span data-stu-id="55b21-141">Method, property, or event</span></span>|<span data-ttu-id="55b21-142">呼び出しが発生したメソッド、プロパティ、またはイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="55b21-142">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="55b21-143">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="55b21-143">Constructor</span></span>|<span data-ttu-id="55b21-144">文字列「.ctor」</span><span class="sxs-lookup"><span data-stu-id="55b21-144">The string ".ctor"</span></span>|  
|<span data-ttu-id="55b21-145">静的コンストラクター</span><span class="sxs-lookup"><span data-stu-id="55b21-145">Static constructor</span></span>|<span data-ttu-id="55b21-146">文字列「.cctor」</span><span class="sxs-lookup"><span data-stu-id="55b21-146">The string ".cctor"</span></span>|  
|<span data-ttu-id="55b21-147">デストラクターです。</span><span class="sxs-lookup"><span data-stu-id="55b21-147">Destructor</span></span>|<span data-ttu-id="55b21-148">文字列「Finalize」</span><span class="sxs-lookup"><span data-stu-id="55b21-148">The string "Finalize"</span></span>|  
|<span data-ttu-id="55b21-149">ユーザー定義の演算子または変換</span><span class="sxs-lookup"><span data-stu-id="55b21-149">User-defined operators or conversions</span></span>|<span data-ttu-id="55b21-150">生成されたメンバー名 (「op_Addition」など)。</span><span class="sxs-lookup"><span data-stu-id="55b21-150">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="55b21-151">Attribute コンストラクター</span><span class="sxs-lookup"><span data-stu-id="55b21-151">Attribute constructor</span></span>|<span data-ttu-id="55b21-152">属性が適用されるメンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="55b21-152">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="55b21-153">属性がメンバー内の要素 (パラメーター、戻り値、ジェネリック型パラメーターなど) である場合、この結果は、その要素に関連付けられているメンバーの名前になります。</span><span class="sxs-lookup"><span data-stu-id="55b21-153">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="55b21-154">含んでいないメンバー (型に適用されているアセンブリ レベルや属性など)</span><span class="sxs-lookup"><span data-stu-id="55b21-154">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="55b21-155">省略可能なパラメーターの既定値。</span><span class="sxs-lookup"><span data-stu-id="55b21-155">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55b21-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="55b21-156">See Also</span></span>  
 <span data-ttu-id="55b21-157">[属性 (Visual Basic)](../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="55b21-157">[Attributes (Visual Basic)](../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="55b21-158"> [一般的な属性 (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="55b21-158"> [Common Attributes (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md) </span></span>  
<span data-ttu-id="55b21-159"> [省略可能なパラメーター](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="55b21-159"> [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md) </span></span>  
<span data-ttu-id="55b21-160"> [プログラミングの概念 (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)</span><span class="sxs-lookup"><span data-stu-id="55b21-160"> [Programming Concepts (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)</span></span>
