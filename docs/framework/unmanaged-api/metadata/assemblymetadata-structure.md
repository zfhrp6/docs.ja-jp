---
title: "ASSEMBLYMETADATA 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 819510c14bd67e7fcc739a19ea945f16b2a66c9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA 構造体
そのバージョンと、ロケール、プロセッサ、およびオペレーティング システムのサポートのレベルを含む、参照先アセンブリに関する情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`usMajorVersion`|参照されたアセンブリのメジャー バージョン番号。 この値を 0 にすることはできません。 場合のすべてのビット`usMajorVersion`が設定された場合、メジャー バージョンが指定されていません。|  
|`usMinorVersion`|参照されたアセンブリのマイナー バージョン番号。 この値を 0 にすることはできません。 場合のすべてのビット`usMinorVersion`は設定されて、マイナー バージョンが指定されていません。|  
|`usBuildNumber`|参照されたアセンブリのビルド番号。 この値を 0 にすることはできません。 場合のすべてのビット`usBuildNumber`が設定された場合、ビルド番号が指定されていません。|  
|`usRevisionNumber`|参照されたアセンブリのリビジョン番号。 この値を 0 にすることはできません。 場合のすべてのビット`usRevisionNumber`は設定されて、リビジョン番号が指定されていません。|  
|`szLocale`|参照されたアセンブリでサポートされているロケールを指定する、セミコロンで区切られた、RFC1766 仕様に準拠しているロケール名の一覧。 Null 値には、ロケールに依存しないことを示します。 **注:** .NET Framework version 1.0 の 2 つ以上のロケールを指定することはできません。|  
|`cbLocale`|ワイド文字単位のサイズ`szLocale`です。|  
|`rdwProcessor`|参照されたアセンブリでサポートされているプロセッサの種類について、Winnt.h で定義されている、識別子の配列。 NULL 値では、プロセッサの独立性を示します。|  
|`ulProcessor`|長さ、`rdwProcessor`配列。|  
|`rOS`|配列[OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)参照されたアセンブリでサポートされているオペレーティング システムを指定するインスタンス。 NULL 値には、オペレーティング システムに依存しないことを示します。|  
|`ulOS`|長さ、`rOS`配列。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [メタデータ構造体](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [OSINFO 構造体](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
