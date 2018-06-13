---
title: ASSEMBLY_INFO 構造体
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ed65181abab58117d539d23fcfeffe71ac19388
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430571"
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
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Fusion.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Fusion 構造体](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [グローバル アセンブリ キャッシュ](../../../../docs/framework/app-domains/gac.md)
