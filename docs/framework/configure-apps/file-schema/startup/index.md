---
title: スタートアップ設定スキーマ
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: 10
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: f344139fd7d7c84aa75ab5e17b6312f3b0c3e031
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="startup-settings-schema"></a>スタートアップ設定スキーマ
スタートアップ設定は、アプリケーションを実行する必要のある共通言語ランタイムのバージョンを指定します。  
  
|要素|説明|  
|-------------|-----------------|  
|[\<requiredRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。 ランタイムのバージョン 1.1 でビルドされたアプリケーションは、**\<supportedRuntime >** 要素を使用します。|  
|[\<supportedRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|アプリケーションでサポートされる共通言語ランタイムのバージョンを指定します。|  
|[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|**\<requiredRuntime>** 要素と **\<supportedRuntime>** 要素を含みます。|  
  
## <a name="see-also"></a>参照  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> 使用するランタイム バージョンの指定](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
