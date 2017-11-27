---
title: ".NET Framework におけるセキュリティの変更点"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
caps.latest.revision: "52"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c1a96e30527aa3da4274ed55059b24aa5a7eeb47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="security-changes-in-the-net-framework"></a>.NET Framework におけるセキュリティの変更点
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] のセキュリティにおける最も重要な変更は、厳密な名前付けの変更です。 これらの変更の詳細については、「 [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) 」を参照してください。  
  
 .NET Framework は、マネージ アプリケーションに 2 階層のセキュリティ モデルを提供します。 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリはリソースへのアクセスを制限する Windows セキュリティ コンテナーで実行されます。 そのコンテナー内では、マネージ アプリケーションは完全に信頼された状態で実行します。 コード アクセス セキュリティの (CAS) の観点からは、権限を昇格するために開発者が実行できる操作はありません。 Windows で与えられる権限の詳細については、Windows デベロッパー センターの「 [App capability declarations (Windows Store apps)](http://go.microsoft.com/fwlink/?LinkId=230436) 」 (アプリの機能宣言 (Windows ストア アプリ)) を参照してください。 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリの作成については、「 [C# または Visual Basic を使った初めての Windows ストア アプリの作成](http://go.microsoft.com/fwlink/?LinkId=230461)」を参照してください。
