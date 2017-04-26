---
title: ".NET Framework 4.6.2 のアプリケーションの互換性 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility,.NET Framework
- application compatibility,.NET Framework 4,6,2
ms.assetid: bdb8335a-a63f-43bb-b978-c1ee92870033
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e34651e87e9c1ccc58472910c0340987da7fc973
ms.lasthandoff: 04/18/2017

---
# <a name="application-compatibility-in-the-net-framework-462"></a>.NET Framework 4.6.2 のアプリケーションの互換性
このトピックでは、.NET Framework 4.6.1 と 4.6.2 間のアプリケーションの互換性の問題に関する情報へのリンクを示します。 問題は 2 つのカテゴリに分けられます。  
  
 [ランタイムの変更点](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)  
 実行時の変更は [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で実行されていて、特定の機能を使用するすべてのアプリに影響します。  
  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)  
 変更の再ターゲットは [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象にして再コンパイルされるアプリに影響します。 Windows コモン コントロールには以下が含まれます。  
  
-   デザイン時環境の変更。 たとえば、ビルド ツールは以前は出力しなかったときに警告を出力する場合があります。  
  
-   ランタイム時環境の変更。 これらは、特に [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリにのみ影響します。 .NET Framework の以前のバージョンを対象とするアプリは、それらのバージョンで実行されているときは以前のように動作します。  
  
 変更の再ターゲットについて説明するトピックでは、次に示すように、予想される影響ごとに個々の項目を分類しました。  
  
 Major  
 これは、多数のアプリに影響するか、またはコードに重大な変更を加える必要のある重要な変更点です。  
  
 Minor  
 これは、少数のアプリに影響するか、またはコードにわずかな変更を加える必要のある変更点です。  
  
 エッジ ケース  
 これは、一般的ではない特定のシナリオでアプリに影響する変更点です。  
  
 透過的  
 これはアプリの開発者やユーザーには大きな影響を及ぼさない変更です。 アプリはこの変更のために変更を加える必要はありません。  
  
## <a name="see-also"></a>関連項目  
 [バージョンおよび依存関係](../../../docs/framework/migration-guide/versions-and-dependencies.md)   
 [4.5.1 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)   
 [4.5.2 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)   
 [4.5 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [4.6 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6.md)   
 [4.6.1 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)   
 [アプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility.md)   
 [GitHub の .NET 4.6.2 の変更リスト](http://go.microsoft.com/fwlink/?LinkId=708778)
 
