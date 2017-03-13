---
title: "COM クラスの例 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "COM, 公開 (Visual C# オブジェクトを)"
  - "例 [C#], COM クラス"
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# COM クラスの例 (C# プログラミング ガイド)
ここでは、COM オブジェクトとして公開されるクラスの例を紹介します。  このコードを .cs ファイルに保存して、プロジェクトに追加後、**\[COM の相互運用機能に登録\]** プロパティを **\[True\]** に設定します。  詳細については、「[NIB: How to: Register a Component for COM Interop](http://msdn.microsoft.com/ja-jp/4de7d474-56e8-4027-994d-d47ca4725c5e)」を参照してください。  
  
 Visual C\# オブジェクトを COM に公開するには、クラス インターフェイス、イベント インターフェイス \(必要な場合\)、およびクラス自体を宣言する必要があります。  クラス メンバーを COM で参照するには、次の規則に従う必要があります。  
  
-   クラスがパブリックであること。  
  
-   プロパティ、メソッド、およびイベントがパブリックであること。  
  
-   プロパティとメソッドがクラス インターフェイスで宣言されていること。  
  
-   イベントがイベント インターフェイスで宣言されていること。  
  
 これらのインターフェイスで宣言されていない、クラス内のほかのパブリック メンバーは、COM から参照されませんが、ほかの .NET Framework オブジェクトからは参照されます。  
  
 プロパティとメソッドを COM に公開するには、それらをクラス インターフェイスで宣言し、`DispId` 属性でマークを付けて、クラスに実装する必要があります。  メンバーをインターフェイスで宣言する順序は、COM の vtable で使用される順序になります。  
  
 クラスのイベントを公開するには、それらをイベント インターフェイスで宣言し、`DispId` 属性でマークを付ける必要があります。  このクラスではこのインターフェイスを実装しないでください。  
  
 クラスによってクラス インターフェイスが実装されます。クラスでは、複数のインターフェイスを実装できますが、最初に実装されるのは既定のクラス インターフェイスです。  ここで、COM に対して公開するメソッドとプロパティを実装します。  このメソッドとプロパティは、パブリックとしてマークされており、クラス インターフェイスの宣言と同じであることが必要です。  また、ここでクラスから発生するイベントを宣言します。  このイベントは、パブリックとしてマークされており、イベント インターフェイスの宣言と同じであることが必要です。  
  
## 使用例  
 [!code-cs[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [相互運用性](../../../csharp/programming-guide/interop/interoperability.md)   
 [\[ビルド\] ページ \(プロジェクト デザイナー\) \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp)