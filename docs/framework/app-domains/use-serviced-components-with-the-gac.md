---
title: "サービス コンポーネントとグローバル アセンブリ キャッシュの使用 | Microsoft Docs"
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
  - "アセンブリ [.NET Framework], グローバル アセンブリ キャッシュ"
  - "GAC (グローバル アセンブリ キャッシュ), サービス コンポーネント"
  - "グローバル アセンブリ キャッシュ, サービス コンポーネント"
  - "サービス コンポーネント, グローバル アセンブリ キャッシュ"
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# サービス コンポーネントとグローバル アセンブリ キャッシュの使用
サービス コンポーネント \(マネージ コード COM\+ コンポーネント\) は、グローバル アセンブリ キャッシュに配置する必要があります。  共通言語ランタイムと COM\+ サービスがグローバル アセンブリ キャッシュ内にないサービス コンポーネントを処理できるシナリオと、処理できないシナリオとがあります。  それぞれのシナリオを次に示します。  
  
-   COM\+ サーバー アプリケーションのサービス コンポーネントの場合、コンポーネントを含むアセンブリは、グローバル アセンブリ キャッシュ内にある必要があります。これは、Dllhost.exe がサービス コンポーネントを格納するディレクトリと同じディレクトリで実行されないためです。  
  
-   COM\+ ライブラリ アプリケーションのサービス コンポーネントの場合、ランタイムと COM\+ サービスは、現在のディレクトリ内を検索することによって、コンポーネントを含むアセンブリへの参照を解決できます。  この場合、アセンブリはグローバル アセンブリ キャッシュ内になくてもかまいません。  
  
-   ASP.NET アプリケーションのサービス コンポーネントの場合、状況は異なります。  サービス コンポーネントを含むアセンブリをアプリケーション ベースの bin ディレクトリに配置してオンデマンド登録を使用する場合、アセンブリはダウンロード キャッシュにシャドウとしてコピーされます。これは、ASP.NET がランタイムのシャドウ機能を利用するためです。  
  
## 参照  
 [How to: Create a Serviced Component](http://msdn.microsoft.com/ja-jp/7ec0b488-e5fc-46f2-a48d-1278ea4e301d)   
 [アセンブリとグローバル アセンブリ キャッシュの使用](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [Gacutil.exe \(グローバル アセンブリ キャッシュ ツール\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)   
 [Assembly Cache Viewer \(Shfusion.dll\)](http://msdn.microsoft.com/ja-jp/0d9464cf-ddba-4ca9-bbec-f678fb58f380)