---
title: "Fusion インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9226eba1b9f03138180430b2abb960f43f4b4260
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="fusion-interfaces"></a>Fusion インターフェイス
このセクションでは、アプリケーションのリソースのプロパティにアクセスして、アプリケーションのリソースの正しいバージョンを見つけるために fusion API が使用するアンマネージ インターフェイスについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [IAppIdAuthority インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 メソッドを生成し、アプリケーションの id と参照キーの比較を提供します。  
  
 [IAssemblyCache インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 グローバル アセンブリ キャッシュの表現を提供します。  
  
 [IAssemblyCacheItem インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 グローバル アセンブリ キャッシュ内の 1 つのアセンブリを表します。  
  
 [IAssemblyEnum インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 配列の列挙子を表す`IAssemblyName`オブジェクト。  
  
 [IAssemblyName インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 記述するおよびアセンブリの一意の id を使用するメソッドを提供します。  
  
 [IDefinitionAppId インターフェイス](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)  
 現在のスコープで、アプリケーションを定義するコードの一意の識別子を表します。  
  
 [IDefinitionIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 現在のスコープで、アプリケーションを定義するコードの一意のシグネチャを表します。  
  
 [IEnumDefinitionIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)  
 コレクションの列挙子の役割を果たす`IDefinitionIdentity`オブジェクト。  
  
 [IEnumIDENTITY_ATTRIBUTE インターフェイス](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)  
 現在のスコープ内のコード オブジェクトの属性の列挙子として機能します。  
  
 [IEnumReferenceIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 コレクションの列挙子の役割を果たす`IReferenceIdentity`オブジェクト。  
  
 [IIdentityAuthority インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 コード オブジェクトの id キーを管理します。  
  
 [IInstallReferenceEnum インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 グローバル アセンブリ キャッシュにインストールされている参照先アセンブリの列挙子を表します。  
  
 [IInstallReferenceItem インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 グローバル アセンブリ キャッシュにインストールされている項目を表します。  
  
 [IReferenceAppId インターフェイス](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)  
 現在のスコープ内のアプリケーションの一意識別子への参照を表します。  
  
 [IReferenceIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)  
 コード オブジェクトの一意のシグネチャへの参照を表します。  
  
## <a name="reference"></a>参照  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a>関連項目  
 [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [Fusion 列挙型](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [Fusion 構造体](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
