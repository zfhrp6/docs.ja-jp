---
title: "スタートアップ設定スキーマ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: 10
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cc014f65cec23f9ab1794d73e0f5d4f7cd5844da
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---
# <a name="startup-settings-schema"></a>スタートアップ設定スキーマ
スタートアップ設定は、アプリケーションを実行する必要のある共通言語ランタイムのバージョンを指定します。  
  
|要素|説明|  
|-------------|-----------------|  
|[\<requiredRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。 ランタイムのバージョン 1.1 でビルドされたアプリケーションは、**\<supportedRuntime >** 要素を使用します。|  
|[\<supportedRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|アプリケーションでサポートされる共通言語ランタイムのバージョンを指定します。|  
|[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|**\<requiredRuntime>** 要素と **\<supportedRuntime>** 要素を含みます。|  
  
## <a name="see-also"></a>関連項目  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver> 使用するランタイム バージョンの指定](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)

