---
title: "AssemblyFlags 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyFlags
helpviewer_keywords: AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 91760b6d16b663257bf3d89915da3bd88b3411bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags 列挙体
アセンブリの実行時の機能を記述する値が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`afImplicitExportedTypes`|アセンブリを構成するファイル内で暗黙的な型定義のエクスポートを指定します。 .NET Framework バージョン 1.0 および 1.1 では、この値は常に設定されると想定します。|  
|`afImplicitResources`|リソース定義がアセンブリを構成するファイル内で暗黙的なことを指定します。 .NET Framework 1.0 および 1.1 では、この値は常に設定されると想定します。|  
|`afNonSideBySideAppDomain`|同じアプリケーション ドメインで実行されている場合に、アセンブリが他のバージョンは実行できないことを指定します。|  
|`afNonSideBySideProcess`|アセンブリはその他のバージョンが同じプロセスで実行されている場合に実行できないことを指定します。|  
|`afNonSideBySideMachine`|アセンブリはその他のバージョンが同じコンピューターで実行されている場合に実行できないことを指定します。|  
  
## <a name="remarks"></a>コメント  
 参照されたアセンブリのサイド バイ サイド互換性機能を記述する 0x0010 ~ 0x0070、包括的な値が使用されます。 これらの値のいずれも設定されている場合、アセンブリがサイド バイ サイド互換性のあると見なされます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MsCorEE.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ列挙体](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
