---
title: "ImportTypes2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportTypes2
api_location: alink.dll
api_type: COM
f1_keywords: ImportTypes2
helpviewer_keywords: ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 61d707cdd827b5e435c961a14e67170ab0e2bc90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="importtypes2-method"></a>ImportTypes2 メソッド
種類のインポートを開始します。 使用してインポートする各スコープの種類のインポートを開始するには、このメソッドを呼び出す[ImportFile メソッド](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a>パラメーター  
 `AssemblyID`  
 インポート先のアセンブリの ID。  
  
 `FileToken`  
 インポート元のファイルの ID です。  
  
 `dwScope`  
 インポート元の 0 から始まるスコープです。  
  
 `phEnum`  
 特定のスコープの種類の列挙子のハンドルを受け取ります。  
  
 `ppImportScope`  
 必要に応じて受信[IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)インターフェイスです。  
  
 `pdwCountOfTypes`  
 必要に応じて指定したスコープの種類の数を受け取ります。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は、S_OK を返します。  
  
## <a name="requirements"></a>要件  
 Alink.h が必要です。  
  
## <a name="see-also"></a>関連項目  
 [IALink2 インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
