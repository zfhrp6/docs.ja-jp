---
title: COR_IL_MAP 構造体
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9676730a4f11ed77996b7a4aab4e538aba9b53c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407363"
---
# <a name="corilmap-structure"></a>COR_IL_MAP 構造体
機能の相対オフセットでの変更を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`oldOffset`|古い Microsoft intermediate language (MSIL) 関数の先頭からの相対オフセットします。|  
|`newOffset`|関数の先頭からの相対新しい MSIL オフセットします。|  
|`fAccurate`|`true` マッピングは正確である既知の場合それ以外の場合、`false`です。|  
  
## <a name="remarks"></a>コメント  
 マップの形式は次のように、: デバッガーと見なされます`oldOffset`、元の未変更の MSIL コード内の MSIL オフセットを参照します。 `newOffset`パラメーターは、新しいでインストルメント化されたコード内の対応する MSIL オフセットを表します。  
  
 正常に動作する、ステップの次の要件を満たす必要があります。  
  
-   マップは、昇順で並べ替えする必要があります。  
  
-   インストルメント化された MSIL コードは並べ替えないでください。  
  
-   元の MSIL コードを削除してはなりません。  
  
-   マップには、プログラム データベース (PDB) ファイルからのすべてのシーケンス ポイントをマップするエントリを含める必要があります。  
  
 存在しないエントリを補間、マップは行いません。 次の例では、マップとその結果を示します。  
  
 マップ:  
  
-   古いオフセットが 0、0 の新しいオフセット  
  
-   古いオフセットが 5、10 個の新しいオフセット  
  
-   古いオフセットを 9、20 の新しいオフセット  
  
 結果:  
  
-   古いオフセットが 0、1、2、3、または 4 は、新しいオフセット 0 にマップされます。  
  
-   古いオフセットが 5、6、7、または 8 は、新しいオフセット 10 にマップされます。  
  
-   9 以降の古いオフセットは、新しいオフセット 20 にマップされます。  
  
-   0、1、2、3、4、5、6、7、8、または 9 の新しいオフセットは、古いオフセット 0 にマップされます。  
  
-   10、11、12、13、14、15、16、17、18 または 19 の新しいオフセットは、古いオフセット 5 にマップされます。  
  
-   20 以上の新しいオフセットは、古いオフセット 9 にマップされます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
