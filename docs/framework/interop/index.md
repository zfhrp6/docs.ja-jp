---
title: "アンマネージ コードとの相互運用 | Microsoft Docs"
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
  - ".NET Framework, 相互運用 (アンマネージ コードとの)"
  - "コンポーネント [.NET Framework], 相互運用 (アンマネージ コードとの)"
  - "相互運用 (アンマネージ コードとの)"
  - "相互運用 (アンマネージ コードとの), 相互運用の概要"
  - "マネージ コード, 相互運用 (アンマネージ コードとの)"
  - "アンマネージ コード"
  - "アンマネージ コード, 相互運用"
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# アンマネージ コードとの相互運用
.NET Framework は、COM コンポーネント、COM\+ サービス、外部のタイプ ライブラリ、および多数のオペレーティング システム サービスとの対話を促進します。  データ型、メソッド シグネチャ、およびエラー処理機構は、マネージ オブジェクト モデルとアンマネージ オブジェクト モデルとでは異なります。  .NET Framework コンポーネントとアンマネージ コードとの相互運用を単純化し、.NET Framework への移行を円滑に行うため、共通言語ランタイムでは、これらのオブジェクト モデルの相違点がクライアントからもサーバーからも認識できないようになっています。  
  
 このランタイムの制御下で実行されるコードをマネージ コードと呼びます。  それに対し、このランタイムの外部で実行されるコードをアンマネージ コードと呼びます。  アンマネージ コードの例としては、COM コンポーネント、ActiveX インターフェイス、Win32 API 関数があります。  
  
## このセクションの内容  
 [Interoperating with Unmanaged Code How\-to Topics](http://msdn.microsoft.com/ja-jp/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 概念を説明したドキュメントに用意されている、アンマネージ コードによる相互運用性に関する方法を説明したトピックへのすべてのリンクを示します。  
  
 [.NET Framework への COM コンポーネントの公開](../../../docs/framework/interop/exposing-com-components.md)  
 .NET Framework アプリケーションから COM コンポーネントを使用する方法について説明します。  
  
 [COM への .NET Framework コンポーネントの公開](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 COM アプリケーションから .NET Framework コンポーネントを使用する方法について説明します。  
  
 [アンマネージ DLL 関数の処理](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 プラットフォーム呼び出しを使ってアンマネージ DLL 関数を呼び出す方法を説明します。  
  
 [相互運用のためのデザインの考慮事項](http://msdn.microsoft.com/ja-jp/b59637f6-fe35-40d6-ae72-901e7a707689)  
 統合される COM コンポーネントを記述するためのヒントを示します。  
  
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)  
 COM 相互運用機能とプラットフォーム呼び出しによるマーシャリングについて説明します。  
  
 [方法: HRESULT に例外を割り当てる](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 例外と HRESULT 間の対応付けについて説明します。  
  
 [Interoperating Using Generic Types](http://msdn.microsoft.com/ja-jp/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 ジェネリック型を COM 相互運用で使用した場合の動作について説明します。  
  
## 関連項目  
 [Advanced COM Interoperability](http://msdn.microsoft.com/ja-jp/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 .NET Framework アプリケーションへの COM コンポーネントの組み込みに関する詳細な情報へのリンクを提供します。