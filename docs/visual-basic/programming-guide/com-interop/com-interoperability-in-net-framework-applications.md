---
title: "COM Interoperability in .NET Framework Applications (Visual Basic) | Microsoft Docs"
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
  - "interoperability, COM and .NET framework objects"
  - "COM interop"
  - "shared components"
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# COM Interoperability in .NET Framework Applications (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

COM オブジェクトと .NET Framework オブジェクトを同じアプリケーションで使用する場合は、オブジェクトをメモリに格納する方法の違いに対処する必要があります。  .NET Framework オブジェクトは、共通言語ランタイムが制御するメモリである、マネージ メモリに格納されます。また、必要に応じて、共通言語ランタイムによって移動される場合があります。  COM オブジェクトは、アンマネージ メモリ内に配置され、他のメモリ位置には移動しません。  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] と [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] には、これらのマネージ コンポーネントとアンマネージ コンポーネントの対話を制御するためのツールが用意されています。  マネージ コードの詳細については、「[共通言語ランタイム](../Topic/Common%20Language%20Runtime%20\(CLR\).md)」を参照してください。  
  
 .NET アプリケーションで COM オブジェクトを利用する以外に、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] を使用して、COM を通じてアンマネージ コードからアクセスできるオブジェクトを作成できます。  
  
 COM と .NET Framework オブジェクトの間の対話の詳細については、このページ内のリンクを参照してください。  
  
## 関連項目  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 COM オブジェクト、ActiveX コントロール、Win32 DLL、マネージ オブジェクト、COM オブジェクトの継承など、Visual Basic での COM 相互運用性に関するトピックへのリンクを提供します。  
  
 [COM Interop Wrapper Error](/visual-cpp/misc/com-interop-wrapper-error)  
 プロジェクト システムが特定のコンポーネントに対して COM 相互運用ラッパーを作成できない場合の結果とオプションについて説明します。  
  
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)  
 マネージ コードとアンマネージ コードの間のやり取りに関するいくつかの問題を簡単に説明し、詳細な情報へのリンクを提供します。  
  
 [COM ラッパー](../Topic/COM%20Wrappers.md)  
 マネージ コードで COM メソッドを呼び出すためのランタイム呼び出し可能ラッパー、および COM クライアントで .NET オブジェクト メソッドを呼び出すための COM 呼び出し可能ラッパーについて説明します。  
  
 [Advanced COM Interoperability](http://msdn.microsoft.com/ja-jp/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 ラッパー、例外、継承、スレッド処理、イベント、変換、およびマーシャリングについて説明している、COM 相互運用に関連するトピックへのリンクを提供します。  
  
 [Tlbimp.exe \(タイプ ライブラリ インポーター\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)  
 COM タイプ ライブラリに含まれる型定義を共通言語ランタイム アセンブリ内の同等の定義に変換するためのツールについて説明します。