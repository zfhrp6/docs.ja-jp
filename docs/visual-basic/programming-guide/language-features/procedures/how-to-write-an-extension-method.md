---
title: '方法: 拡張メソッドを作成する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: e220a025c39757b492be033caeb8924523515804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="127ce-102">方法: 拡張メソッドを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="127ce-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="127ce-103">拡張メソッドを使用すると、既存のクラスにメソッドを追加できます。</span><span class="sxs-lookup"><span data-stu-id="127ce-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="127ce-104">そのクラスのインスタンスの場合と同様、拡張メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="127ce-104">The extension method can be called as if it were an instance of that class.</span></span>  
  
### <a name="to-define-an-extension-method"></a><span data-ttu-id="127ce-105">拡張メソッドを定義するには</span><span class="sxs-lookup"><span data-stu-id="127ce-105">To define an extension method</span></span>  
  
1.  <span data-ttu-id="127ce-106">Visual Studio で新規または既存の Visual Basic アプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="127ce-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="127ce-107">拡張メソッドを定義するファイルの上部には、次の import ステートメントを含めます。</span><span class="sxs-lookup"><span data-stu-id="127ce-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  <span data-ttu-id="127ce-108">新規または既存のアプリケーションでのモジュール内で拡張機能の属性を持つメソッドの定義を開始します。</span><span class="sxs-lookup"><span data-stu-id="127ce-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>  
  
    ```  
    <Extension()>  
    ```  
  
4.  <span data-ttu-id="127ce-109">最初のパラメーターの型が拡張するデータ型にする必要がある点を除いて、通常の方法でメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="127ce-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a><span data-ttu-id="127ce-110">例</span><span class="sxs-lookup"><span data-stu-id="127ce-110">Example</span></span>  
 <span data-ttu-id="127ce-111">次の例は、モジュールの拡張メソッドを宣言`StringExtensions`です。</span><span class="sxs-lookup"><span data-stu-id="127ce-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="127ce-112">2 番目のモジュール`Module1`、インポート`StringExtensions`メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="127ce-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="127ce-113">拡張メソッドが呼び出されるとスコープ内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="127ce-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="127ce-114">拡張メソッド`PrintAndPunctuate`拡張、<xref:System.String>文字列インスタンスを表示するメソッドを持つクラスが続くでパラメーターとして送信される区切り記号の文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="127ce-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>  
  
```vb  
' Declarations will typically be in a separate module.  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
```vb  
' Import the module that holds the extension method you want to use,   
' and call it.  
  
Imports ConsoleApplication2.StringExtensions  
  
Module Module1  
  
    Sub Main()  
        Dim example = "Hello"  
        example.PrintAndPunctuate("?")  
        example.PrintAndPunctuate("!!!!")  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="127ce-115">メソッドが 2 つのパラメーターで定義されているし、1 つだけ備えたと呼ばれることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="127ce-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="127ce-116">最初のパラメーターでは、 `aString`、メソッド定義にバインドされている`example`のインスタンス`String`メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="127ce-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="127ce-117">この例の出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="127ce-117">The output of the example is as follows:</span></span>  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="127ce-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="127ce-118">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [<span data-ttu-id="127ce-119">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="127ce-119">Extension Methods</span></span>](./extension-methods.md)  
 [<span data-ttu-id="127ce-120">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="127ce-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="127ce-121">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="127ce-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="127ce-122">Visual Basic におけるスコープ</span><span class="sxs-lookup"><span data-stu-id="127ce-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
