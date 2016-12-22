---
title: "Introduction to COM Interop (Visual Basic) | Microsoft Docs"
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
  - "interop assemblies"
  - "COM interop, about COM interop"
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Introduction to COM Interop (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

コンポーネント オブジェクト モデル \(COM: Component Object Model\) を使用することによって、オブジェクトはその機能を他のコンポーネントやホスト アプリケーションに公開できます。  COM オブジェクトは長年にわたり Windows プログラミングの基盤として使用されてきましたが、共通言語ランタイム \(CLR: Common Language Runtime\) 用に設計されたアプリケーションには多数の利点があります。  
  
 COM で開発されたアプリケーションは今後置き換えられ、最終的には [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] アプリケーションが使われるようになると考えられます。  しかし、それまでは [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] で COM オブジェクトを使用または作成することが必要な場合があります。  COM との相互運用性、つまり *COM 相互運用機能*によって、既存の COM オブジェクトを使用しながら、独自のペースで [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] に移行していくことができます。  
  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] を使用して COM コンポーネントを作成すると、登録を必要としない COM 相互運用機能を利用できます。  これによって、複数のバージョンの DLL がコンピューターにインストールされている場合に、どの DLL バージョンを有効にするのかを制御できます。エンド ユーザーは、XCOPY または FTP を使用して、アプリケーションを実行できる自分のコンピューター上の適切なディレクトリにコピーできます。  詳細については、「[登録を必要としない COM 相互運用機能](../Topic/Registration-Free%20COM%20Interop.md)」を参照してください。  
  
## マネージ コードとマネージ データ  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 用に開発されたコードを*マネージ コード*と呼びます。マネージ コードには、CLR によって使用されるメタデータが含まれます。  [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] アプリケーションによって使用されるデータを*マネージ データ*と呼びます。これは、メモリの割り当ておよび再要求、型チェックの実行などのデータ関連のタスクが、ランタイムによって管理されるためです。  [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] では既定でマネージ コードとマネージ データが使用されますが、相互運用機能アセンブリ \(このページの後半で説明します\) を使用することによって、COM オブジェクトのアンマネージ コードとアンマネージ データにアクセスできます。  
  
## アセンブリ  
 アセンブリとは、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] アプリケーションの主要なビルド ブロックです。  アセンブリは機能の集合体であり、1 つ以上のファイルで構成される単一の実装ユニットとしてビルド、バージョン管理、および配置されます。  各アセンブリにはアセンブリ マニフェストが含まれます。  
  
## タイプ ライブラリとアセンブリ マニフェスト  
 タイプ ライブラリは、メンバーの名前やデータ型など、COM オブジェクトの特性を記述します。  アセンブリ マニフェストは、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] アプリケーションについて同様の機能を果たします。  これらに含まれている情報は次のとおりです。  
  
-   アセンブリの ID、バージョン、カルチャ、およびデジタル署名。  
  
-   アセンブリ実装を構成するファイル。  
  
-   アセンブリを構成する型およびリソース。  アセンブリからエクスポートされる型およびリソースも含まれます。  
  
-   その他のアセンブリへのコンパイル時の依存関係。  
  
-   アセンブリを正常に実行するために必要なアクセス許可。  
  
 アセンブリおよびアセンブリ マニフェストの詳細については、「[アセンブリとグローバル アセンブリ キャッシュ](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
### タイプ ライブラリのインポートとエクスポート  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] には Tlbimp ユーティリティがあります。Tlbimp を使用すると、タイプ ライブラリから [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] アプリケーションに情報をインポートできます。  また、Tlbexp ユーティリティを使用して、アセンブリからタイプ ライブラリを生成できます。  
  
 Tlbimp および Tlbexp の詳細については、「[Tlbimp.exe \(タイプ ライブラリ インポーター\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)」および「[Tlbexp.exe \(タイプ ライブラリ エクスポーター\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md)」を参照してください。  
  
## 相互運用アセンブリ  
 相互運用機能アセンブリは、マネージ コードとアンマネージ コードを仲介する [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] アセンブリであり、それに対応する [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] マネージ メンバーに COM オブジェクト メンバーを割り当てます。  [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] によって作成される相互運用機能アセンブリは、相互運用性のマーシャリングなど、COM オブジェクトの操作で発生する詳細な作業の多くを処理します。  
  
## 相互運用性のマーシャリング  
 すべての [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] アプリケーションは、使用するプログラミング言語の種類に関係なく、オブジェクトを相互運用できるようにするための共通の型セットを共有します。  COM オブジェクトのパラメーターおよび戻り値の型は、マネージ コードで使用されるデータ型とは異なることがあります。  *相互運用性*のマーシャリングとは、COM オブジェクトからマネージ コードへの変換およびマネージ コードから COM オブジェクトへの変換のときに、パラメーターと戻り値を対応するデータ型にパッケージ化する処理です。  詳細については、「[相互運用マーシャリング](../Topic/Interop%20Marshaling.md)」を参照してください。  
  
## 参照  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [アンマネージ コードとの相互運用](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)   
 [アセンブリとグローバル アセンブリ キャッシュ](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Tlbimp.exe \(タイプ ライブラリ インポーター\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [Tlbexp.exe \(タイプ ライブラリ エクスポーター\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md)   
 [相互運用マーシャリング](../Topic/Interop%20Marshaling.md)   
 [登録を必要としない COM 相互運用機能](../Topic/Registration-Free%20COM%20Interop.md)