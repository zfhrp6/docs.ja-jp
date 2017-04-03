---
title: "方法: CLS 準拠でない例外をキャッチする | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 8
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3515ecab379a0e910cdd5ba82a4a39b085cc816f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-catch-a-non-cls-exception"></a>方法 : CLS 準拠でない例外をキャッチする
C++/CLI をはじめとする一部の .NET 言語では、<xref:System.Exception> から派生していない例外をオブジェクトでスローすることができます。 このような例外は "*CLS 準拠でない例外*" や "*非例外*" と呼ばれています。 [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] では、CLS 準拠でない例外をスローすることはできませんが、それらをキャッチすることはできます。次の 2 とおりの方法があります。  
  
-   `catch (Exception e)` ブロック内で <xref:System.Runtime.CompilerServices.RuntimeWrappedException> としてキャッチする。  
  
     [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] アセンブリの既定の動作上、CLS 準拠でない例外はラップされた例外としてキャッチされます。 この方法は、元の例外にアクセスする必要がある場合に使用します。<xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> プロパティから元の例外にアクセスすることができます。 この方法で例外をキャッチする方法については、このトピックで後述します。  
  
-   `catch (Exception)` ブロックまたは `catch (Exception e)` ブロックの後に置いた汎用的な catch ブロック (例外の型が指定されていない catch ブロック) 内でキャッチする。  
  
     この方法は、CLS 準拠でない例外への応答として何らかのアクション (ログ ファイルへの書き込みなど) を実行したい場合で、なおかつ例外情報にアクセスする必要がない場合に使用します。 既定では、すべての例外が共通言語ランタイムによってラップされます。 この動作を無効にするには、`[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]` というアセンブリ レベルの属性を (通常、AssemblyInfo.cs ファイル内の) コードに追加します。  
  
### <a name="to-catch-a-non-cls-exception"></a>CLS 準拠でない例外をキャッチするには  
  
1.  `catch(Exception e) block` 内で、`as` キーワードを使用するか、または `e` を <xref:System.Runtime.CompilerServices.RuntimeWrappedException> にキャストできるかどうかを調べます。  
  
2.  <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> プロパティから元の例外にアクセスします。  
  
## <a name="example"></a>例  
 次の例は、C++/CLR のクラス ライブラリからスローされた、CLS 準拠でない例外をキャッチする方法を示しています。 この例で、[!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] クライアント コードは、スローされる例外の型が <xref:System.String?displayProperty=fullName> であることを事前に把握しています。 <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> プロパティの本来の型が自分のコードからアクセスできる型であれば、プロパティを元の型にキャストすることができます。  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>   
 [例外と例外処理](../../../csharp/programming-guide/exceptions/index.md)
