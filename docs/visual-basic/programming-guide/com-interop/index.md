---
title: "COM Interop (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, COM interop"
  - "COM interop, in Visual Basic"
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# COM Interop (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

コンポーネント オブジェクト モデル \(COM: Component Object Model\) を使用することによって、オブジェクトはその機能をその他のコンポーネントやホスト アプリケーションに公開できます。  今日のほとんどのソフトウェアでは、COM オブジェクトが使用されています。  .NET アセンブリは新規アプリケーションにとって最善の選択肢ですが、COM オブジェクトを使用する必要のある場合もあります。  ここでは、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] での COM オブジェクトの作成と使用に関連する問題について説明します。  
  
## このセクションの内容  
 [Introduction to COM Interop](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 COM 相互運用性の概要を説明します。  
  
 [How to: Reference COM Objects from Visual Basic](../Topic/How%20to:%20Reference%20COM%20Objects%20from%20Visual%20Basic.md)  
 タイプ ライブラリのある COM オブジェクトに参照を追加する方法を説明します。  
  
 [How to: Work with ActiveX Controls](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 既存の ActiveX コントロールを使用して [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ツールボックスに機能を追加する方法を説明します。  
  
 [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 Windows オペレーティング システムに含まれる API を呼び出す手順について説明します。  
  
 [How to: Call Windows APIs](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 User32.dll の `MessageBox` 関数を定義し、呼び出す方法を説明します。  
  
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 符号なしの型パラメーターを持つ Windows の関数を呼び出す方法を示します。  
  
 [Walkthrough: Creating COM Objects with Visual Basic](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 COM クラス テンプレートを使用する場合と使用しない場合の COM オブジェクトの作成手順を説明します。  
  
 [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 COM を使用する際、発生する可能性のある問題について説明します。  
  
 [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 1 つのアプリケーションで COM オブジェクトと .NET Framework オブジェクトを同時に使用する方法について簡単に説明します。  
  
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 既存の COM オブジェクトを新しいオブジェクトの基礎として使用する方法について説明します。  
  
## 関連項目  
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)  
 共通言語ランタイムによって提供される相互運用性サービスについて説明します。  
  
 [.NET Framework への COM コンポーネントの公開](../Topic/Exposing%20COM%20Components%20to%20the%20.NET%20Framework.md)  
 COM 相互運用機能を通じて COM の型を呼び出す手順を説明します。  
  
 [COM への .NET Framework コンポーネントの公開](../Topic/Exposing%20.NET%20Framework%20Components%20to%20COM.md)  
 COM からのマネージ型の準備および使用方法について説明します。  
  
 [相互運用固有の属性の適用](../Topic/Applying%20Interop%20Attributes.md)  
 アンマネージ コードと相互運用するときに使用できる属性について説明します。