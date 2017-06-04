---
title: "COM 相互運用機能によるデータのマーシャリング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM 相互運用機能, データ マーシャリング"
  - "マーシャリング (データの), COM 相互運用機能"
ms.assetid: 0bcdd7bf-5026-43eb-b08b-f03f90db9df9
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# COM 相互運用機能によるデータのマーシャリング
COM 相互運用は、マネージ コードから COM オブジェクトを使用すること、およびマネージ オブジェクトを COM に公開することの、両方の操作をサポートします。  COM との間でデータをマーシャリングする操作のサポートは広範で、ほとんどの場合、正しいマーシャリング動作が提供されます。  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] には、以下の COM 相互運用ツールが含まれています。  
  
-   [タイプ ライブラリ インポーター \(Tlbimp.exe\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)、これは COM タイプ ライブラリを相互運用アセンブリに変換します。  このアセンブリから、相互運用マーシャリング サービスは、マネージ メモリとアンマネージ メモリ間のデータ マーシャリングを実行するラッパーを生成します。  
  
-   [タイプ ライブラリ エクスポーター \(Tlbexp.exe\)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)、これは COM タイプ ライブラリをアセンブリから生成して、メソッド呼び出しの際にマーシャリングを実行するラッパーを生成します。  
  
 このセクションでは、マーシャラーに追加の型情報を提供できる \(またはその必要がある\) ときに、相互運用ラッパーをカスタマイズするためのプロセスについて説明します。  
  
## このセクションの内容  
 [COM のデータ型](http://msdn.microsoft.com/ja-jp/f93ae35d-a416-4218-8700-c8218cc90061)  
 対応するマネージとアンマネージのデータ型を提供します。  
  
 [COM 呼び出し可能ラッパーのカスタマイズ](http://msdn.microsoft.com/ja-jp/825177d3-4b2c-4723-82be-ce6ca2c34ace)  
 デザイン時に **MarshalAsAttribute** 属性を使用して、データ型を明示的にマーシャリングする方法について説明します。  
  
 [ランタイム呼び出し可能ラッパーのカスタマイズ](http://msdn.microsoft.com/ja-jp/4652beaf-77d0-4f37-9687-ca193288c0be)  
 相互運用アセンブリで型のマーシャリング動作を調整する方法、および COM 型を手動で定義する方法について説明します。  
  
 [方法: マネージ コード DCOM を WCF に移行する](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 最も安全なソリューションのために、マネージ DCOM コードを WCF に移行する方法について説明します。  
  
## 関連項目  
 [Advanced COM Interoperability](http://msdn.microsoft.com/ja-jp/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 .NET Framework アプリケーションに COM コンポーネントを組み込む方法についての詳細情報へのリンクを示します。  
  
 [Assembly to Type Library Conversion Summary](http://msdn.microsoft.com/ja-jp/3a37eefb-a76c-4000-9080-7dbbf66a4896)  
 アセンブリからタイプ ライブラリにエクスポート変換するプロセスについて説明します。  
  
 [Type Library to Assembly Conversion Summary](http://msdn.microsoft.com/ja-jp/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 タイプ ライブラリからアセンブリにインポート変換するプロセスについて説明します。  
  
 [Interoperating Using Generic Types](http://msdn.microsoft.com/ja-jp/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 COM 相互運用性のジェネリック型を使用するとき、どのアクションがサポートされるかについて説明します。