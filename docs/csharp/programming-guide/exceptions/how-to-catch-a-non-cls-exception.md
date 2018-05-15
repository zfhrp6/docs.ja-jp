---
title: '方法 : CLS 準拠でない例外をキャッチする'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 8
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5647fc8501afe2a4bf74739fd8efd4e6b74559a2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="205dc-102">方法 : CLS 準拠でない例外をキャッチする</span><span class="sxs-lookup"><span data-stu-id="205dc-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="205dc-103">C++/CLI をはじめとする一部の .NET 言語では、<xref:System.Exception> から派生していない例外をオブジェクトでスローすることができます。</span><span class="sxs-lookup"><span data-stu-id="205dc-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="205dc-104">このような例外は "*CLS 準拠でない例外*" や "*非例外*" と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="205dc-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="205dc-105">Visual C# では、CLS 準拠でない例外をスローすることはできませんが、それらをキャッチすることはできます。次の 2 とおりの方法があります。</span><span class="sxs-lookup"><span data-stu-id="205dc-105">In Visual C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
-   <span data-ttu-id="205dc-106"><xref:System.Runtime.CompilerServices.RuntimeWrappedException> として `catch (Exception e)` ブロック内で。</span><span class="sxs-lookup"><span data-stu-id="205dc-106">Within a `catch (Exception e)` block as a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
     <span data-ttu-id="205dc-107">Visual C# アセンブリの既定の動作上、CLS 準拠でない例外はラップされた例外としてキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="205dc-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="205dc-108">元の例外にアクセスする必要がある場合 (<xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> プロパティからアクセスできます)、このメソッドを利用します。</span><span class="sxs-lookup"><span data-stu-id="205dc-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span> <span data-ttu-id="205dc-109">この方法で例外をキャッチする方法については、このトピックで後述します。</span><span class="sxs-lookup"><span data-stu-id="205dc-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
-   <span data-ttu-id="205dc-110">`catch (Exception)` ブロックまたは `catch (Exception e)` ブロックの後に置いた汎用的な catch ブロック (例外の型が指定されていない catch ブロック) 内でキャッチする。</span><span class="sxs-lookup"><span data-stu-id="205dc-110">Within a general catch block (a catch block without an exception type specified) that is put after a `catch (Exception)` or `catch (Exception e)` block.</span></span>  
  
     <span data-ttu-id="205dc-111">この方法は、CLS 準拠でない例外への応答として何らかのアクション (ログ ファイルへの書き込みなど) を実行したい場合で、なおかつ例外情報にアクセスする必要がない場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="205dc-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="205dc-112">既定では、すべての例外が共通言語ランタイムによってラップされます。</span><span class="sxs-lookup"><span data-stu-id="205dc-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="205dc-113">この動作を無効にするには、`[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]` というアセンブリ レベルの属性を (通常、AssemblyInfo.cs ファイル内の) コードに追加します。</span><span class="sxs-lookup"><span data-stu-id="205dc-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="205dc-114">CLS 準拠でない例外をキャッチするには</span><span class="sxs-lookup"><span data-stu-id="205dc-114">To catch a non-CLS exception</span></span>  
  
1.  <span data-ttu-id="205dc-115">`catch(Exception e) block` 内で、`as` キーワードを利用し、`e` を <xref:System.Runtime.CompilerServices.RuntimeWrappedException> にキャストできるかどうかテストします。</span><span class="sxs-lookup"><span data-stu-id="205dc-115">Within a `catch(Exception e) block`, use the `as` keyword to test whether `e` can be cast to a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
2.  <span data-ttu-id="205dc-116"><xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> プロパティから元の例外にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="205dc-116">Access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="205dc-117">例</span><span class="sxs-lookup"><span data-stu-id="205dc-117">Example</span></span>  
 <span data-ttu-id="205dc-118">次の例は、C++/CLR のクラス ライブラリからスローされた、CLS 準拠でない例外をキャッチする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="205dc-118">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLR.</span></span> <span data-ttu-id="205dc-119">この例で、Visual C# クライアント コードは、スローされる例外の型が <xref:System.String?displayProperty=nameWithType> であることを事前に把握しています。</span><span class="sxs-lookup"><span data-stu-id="205dc-119">Note that in this example, the Visual C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="205dc-120">その型にコードからアクセスできる限り、<xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> プロパティは元の型にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="205dc-120">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property back its original type as long as that type is accessible from your code.</span></span>  
  
```  
// Class library written in C++/CLR.  
   ThrowNonCLS.Class1 myClass = new ThrowNonCLS.Class1();  
  
   try  
   {  
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();   
   }  
  
   catch (Exception e)  
   {  
    RuntimeWrappedException rwe = e as RuntimeWrappedException;  
    if (rwe != null)      
    {  
      String s = rwe.WrappedException as String;  
      if (s != null)  
      {  
        Console.WriteLine(s);  
      }  
    }  
    else  
    {  
       // Handle other System.Exception types.  
    }  
   }             
```  
  
## <a name="see-also"></a><span data-ttu-id="205dc-121">参照</span><span class="sxs-lookup"><span data-stu-id="205dc-121">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>  
 [<span data-ttu-id="205dc-122">例外と例外処理</span><span class="sxs-lookup"><span data-stu-id="205dc-122">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
