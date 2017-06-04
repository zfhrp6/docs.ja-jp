---
title: ".NET Framework 4.5.1 のアプリケーションの互換性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b07b729-e2bf-4925-8b83-9c9ee6c48612
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# .NET Framework 4.5.1 のアプリケーションの互換性
このトピックでは、.NET Framework 4.5 と 4.5.1 間のアプリケーションの互換性の問題に関する情報へのリンクを示します。  問題は 2 つのカテゴリに分けられます。  
  
 [Runtime changes \(実行時の変更\)](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)  
 実行時の変更は [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] で実行されていて、特定の機能を使用するすべてのアプリに影響します。  
  
 [Retargeting changes \(変更の再ターゲット\)](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-5-1.md)  
 変更の再ターゲットは [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] を対象にして再コンパイルされるアプリに影響します。  Windows コモン コントロールには以下が含まれます。  
  
-   デザイン時環境の変更。  たとえば、ビルド ツールは以前は出力しなかったときに警告を出力する場合があります。  
  
-   ランタイム時環境の変更。  これらは、特に [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] を対象とするアプリにのみ影響します。  .NET Framework の以前のバージョンを対象とするアプリは、それらのバージョンで実行されているときは以前のように動作します。  
  
 ランタイムの変更および変更の再ターゲットについて説明するトピックでは、次に示すように、予想される影響ごとに個々の項目を分類しました。  
  
 Major  
 これは、多数のアプリに影響するか、またはコードに重大な変更を加える必要のある重要な変更点です。  
  
 Minor  
 これは、少数のアプリに影響するか、またはコードにわずかな変更を加える必要のある変更点です。  
  
 エッジ ケース  
 これは、一般的ではない特定のシナリオでアプリに影響する変更点です。  
  
 透過的  
 これはアプリの開発者やユーザーには大きな影響を及ぼさない変更です。  アプリはこの変更のために変更を加える必要はありません。  
  
## 参照  
 [バージョンおよび依存関係](../../../docs/framework/migration-guide/versions-and-dependencies.md)   
 [アプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility.md)   
 [4.5 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [4.5.2 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)