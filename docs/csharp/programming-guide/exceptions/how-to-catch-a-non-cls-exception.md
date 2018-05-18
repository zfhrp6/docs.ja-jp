---
title: '方法 : CLS 準拠でない例外をキャッチする'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 6169f4b6de2efdfed0dbf43272d708c47b46dbca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-catch-a-non-cls-exception"></a>方法 : CLS 準拠でない例外をキャッチする
C++/CLI をはじめとする一部の .NET 言語では、<xref:System.Exception> から派生していない例外をオブジェクトでスローすることができます。 このような例外は "*CLS 準拠でない例外*" や "*非例外*" と呼ばれています。 Visual C# では、CLS 準拠でない例外をスローすることはできませんが、それらをキャッチすることはできます。次の 2 とおりの方法があります。  
  
-   <xref:System.Runtime.CompilerServices.RuntimeWrappedException> として `catch (Exception e)` ブロック内で。  
  
     Visual C# アセンブリの既定の動作上、CLS 準拠でない例外はラップされた例外としてキャッチされます。 元の例外にアクセスする必要がある場合 (<xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> プロパティからアクセスできます)、このメソッドを利用します。 この方法で例外をキャッチする方法については、このトピックで後述します。  
  
-   `catch (Exception)` ブロックまたは `catch (Exception e)` ブロックの後に置いた汎用的な catch ブロック (例外の型が指定されていない catch ブロック) 内でキャッチする。  
  
     この方法は、CLS 準拠でない例外への応答として何らかのアクション (ログ ファイルへの書き込みなど) を実行したい場合で、なおかつ例外情報にアクセスする必要がない場合に使用します。 既定では、すべての例外が共通言語ランタイムによってラップされます。 この動作を無効にするには、`[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]` というアセンブリ レベルの属性を (通常、AssemblyInfo.cs ファイル内の) コードに追加します。  
  
### <a name="to-catch-a-non-cls-exception"></a>CLS 準拠でない例外をキャッチするには  
  
1.  `catch(Exception e) block` 内で、`as` キーワードを利用し、`e` を <xref:System.Runtime.CompilerServices.RuntimeWrappedException> にキャストできるかどうかテストします。  
  
2.  <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> プロパティから元の例外にアクセスします。  
  
## <a name="example"></a>例  
 次の例は、C++/CLR のクラス ライブラリからスローされた、CLS 準拠でない例外をキャッチする方法を示しています。 この例で、Visual C# クライアント コードは、スローされる例外の型が <xref:System.String?displayProperty=nameWithType> であることを事前に把握しています。 その型にコードからアクセスできる限り、<xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> プロパティは元の型にキャストできます。  
  
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
  
## <a name="see-also"></a>参照  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>  
 [例外と例外処理](../../../csharp/programming-guide/exceptions/index.md)
