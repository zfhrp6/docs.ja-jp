---
title: IMetaDataTables::GetRow メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 954b4df6b341e18c5a995b57541a72e236278c45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatablesgetrow-method"></a>IMetaDataTables::GetRow メソッド
指定したテーブルのインデックスにある表で、指定した行のインデックス行を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ixTbl`  
 [in]行の取得元となるテーブルのインデックス。  
  
 `rid`  
 [in]取得する行のインデックス。  
  
 `ppRow`  
 [out]行へのポインターへのポインター。  
  
## <a name="remarks"></a>コメント  
 このメソッドの使用方法は、一貫性のある結果を返さないためお勧めしませんしないでください。 GUID のテーブルについては、共通言語基盤 (CLI) ドキュメント、特に「Partition II:: Metadata Definition and Semantics」を参照してください。 ドキュメントはオンラインで入手できます。MSDN の「[ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212)」 (ECMA の C# および共通言語基盤の標準規格) と、ECMA のインターナショナル Web サイトにある「[Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552)」を参照してください。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataTables インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [IMetaDataTables2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
