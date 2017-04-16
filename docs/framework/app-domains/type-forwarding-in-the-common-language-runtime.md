---
title: "共通言語ランタイムでの型の転送 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アセンブリ [.NET Framework]、型の転送"
  - "型の転送"
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# 共通言語ランタイムでの型の転送
型の転送を使用すると、別のアセンブリに型を移動する際に、元のアセンブリを使用するアプリケーションを再コンパイルする必要がありません。  
  
 たとえば、`Utility.dll` というアセンブリ内の `Example` クラスをアプリケーションが使用しているとします。  `Utility.dll` の開発者がアセンブリをリファクタリングすることになり、その過程で `Example` クラスを別のアセンブリに移動します。  `Utility.dll` の前のバージョンが `Utility.dll` の新しいバージョンとそのコンパニオン アセンブリで置換されると、`Example` クラスを使用するアプリケーションは、新しいバージョンの `Utility.dll` で `Example` クラスを見つけられないために失敗します。  
  
 これを回避するために、`Utility.dll` の開発者は <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 属性を使用して、`Example` クラスに対する要求を転送します。  この属性が新しいバージョンの `Utility.dll` に適用されている場合は、`Example` クラスに対する要求が現在このクラスを含んでいるアセンブリに転送されます。  既存のアプリケーションは、再コンパイルを必要とすることなく正常に機能し続けます。  
  
> [!NOTE]
>  .NET Framework Version 2.0 では、Visual Basic で作成されたアセンブリから型を転送できません。  ただし、Visual Basic で作成されたアプリケーションでは、転送された型を使用できます。  つまり、アプリケーションが C\# または C\+\+ で作成されたアセンブリを使用している場合は、そのアセンブリの型が別のアセンブリに転送されても、Visual Basic アプリケーションは転送された型を使用できます。  
  
## 型の転送  
 型の転送は 4 つの手順で行います。  
  
1.  型のソース コードを、元のアセンブリから転送先のアセンブリに移動します。  
  
2.  型の元の場所であるアセンブリで、移動された型に対して <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> を追加します。  次のコードは、移動された `Example` という型の属性を示しています。  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp#  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  型の現在の場所であるアセンブリをコンパイルします。  
  
4.  型の元の場所であるアセンブリを、型の現在の場所であるアセンブリへの参照を指定して再コンパイルします。  たとえば、C\# ファイルをコマンド ラインからコンパイルする場合は、[\/reference \(Import Metadata\)](../Topic/-reference%20\(C%23%20Compiler%20Options\).md) オプションを使用して型の現在の場所であるアセンブリを指定します。  C\+\+ では、ソース ファイルで [\#using](../Topic/%23using%20Directive%20\(C++\).md) ディレクティブを使用して、型の現在の場所であるアセンブリを指定します。  
  
## 参照  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Type Forwarding \(C\+\+\/CLI\)](../Topic/Type%20Forwarding%20\(C++-CLI\).md)   
 [\#using ディレクティブ](../Topic/%23using%20Directive%20\(C++\).md)