---
title: "ASSEMBLY_INFO 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLY_INFO
api_location: fusion.dll
api_type: COM
f1_keywords: ASSEMBLY_INFO
helpviewer_keywords: ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d532bbd2d338f942c09c4213620468a3361db5f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyinfo-structure"></a>ASSEMBLY_INFO 構造体
グローバル アセンブリ キャッシュに登録されているアセンブリに関する情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`cbAssemblyInfo`|構造体のバイト単位のサイズ。 このフィールドは、将来の機能拡張予約されています。|  
|`dwAssemblyFlags`|アセンブリのインストールの詳細を示すフラグです。 次の値がサポートされています。<br /><br /> -ASSEMBLYINFO_FLAG_INSTALLED 値アセンブリがインストールされていることを示します。 .NET Framework の現在のバージョンが常に設定`dwAssemblyFlags`この値にします。<br />-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT 値アセンブリが常駐ペイロードであることを示します。 .NET Framework の現在のバージョンを設定しません`dwAssemblyFlags`この値にします。|  
|`uliAssemblySizeInKB`|アセンブリに含まれるファイルの合計サイズ。|  
|`pszCurrentAssemblyPathBuf`|マニフェスト ファイルに、現在のパスを格納する文字列バッファーへのポインター。 パスの末尾に null 文字を使用する必要があります。|  
|`cchBuf`|ワイド文字で、null 終端文字の数を`pszCurrentAssemblyPathBuf`が含まれています。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Fusion.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Fusion 構造体](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [グローバル アセンブリ キャッシュ](../../../../docs/framework/app-domains/gac.md)
