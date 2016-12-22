---
title: "方法 : CLS 準拠でない例外をキャッチする | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "例外 [C#], 非 CLS"
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : CLS 準拠でない例外をキャッチする
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\+\+、CLI を含む一部の .NET 言語では、オブジェクトは、<xref:System.Exception> から派生していない例外をスローできます。  このような例外を*CLS 準拠でない例外*、または *Exception クラスから派生していない例外*と呼びます。  [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] では、CLS 準拠でない例外をスローすることはできませんが、これらの例外を次の 2 とおりの方法でキャッチできます。  
  
-   `catch (Exception e)` ブロック内で <xref:System.Runtime.CompilerServices.RuntimeWrappedException> としてキャッチ。  
  
     既定では、[!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] アセンブリは CLS 準拠でない例外をラップされた例外としてキャッチします。  <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> プロパティからアクセスできる元の例外にアクセスする必要がある場合は、この方法を使用します。  この方法で例外をキャッチする方法については、このトピックで後述する手順で説明します。  
  
-   `catch (Exception)` ブロックか `catch (Exception e)` ブロックの後ろに置かれた汎用の catch ブロック \(例外の型が指定されていない catch ブロック\) 内でキャッチ。  
  
     CLS 準拠でない例外に対して何らかのアクションを実行する必要があり、例外情報にアクセスする必要がない場合は、この方法を使用します。  既定では、共通言語ランタイムはすべての例外をラップします。  この動作を無効にするには、アセンブリレベルの属性 `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]` をコード ファイル \(厳密には AssemblyInfo.cs ファイル\) に追加します。  
  
### CLS 準拠でない例外をキャッチするには  
  
1.  `catch(Exception e) block`内で `as` キーワードを使用して、`e` を <xref:System.Runtime.CompilerServices.RuntimeWrappedException> にキャストできるかどうかをテストします。  
  
2.  <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> プロパティから元の例外にアクセスします。  
  
## 使用例  
 次の例では、C\+\+ または CLR で記述されたクラス ライブラリからスローされた CLS 準拠でない例外をキャッチする方法を示します。  この例では、[!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] クライアント コードは、スローされる例外の型が <xref:System.String?displayProperty=fullName> であることを事前に認識しています。  コードからこの型にアクセスできる場合は、<xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> プロパティを元の型にキャストできます。  
  
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
  
## 参照  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>   
 [例外と例外処理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)