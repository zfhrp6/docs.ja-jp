---
title: "ImportFile2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile2
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile2
helpviewer_keywords: ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4d7e842152e84992124ec29cd551c3b5d50a6d61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="importfile2-method"></a>ImportFile2 メソッド
アセンブリとバインドされていないモジュールをインポートします。 同様に、このメソッドは[ImportFile メソッド](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)、いますが、インポートするファイルがディスクに存在しない場合でも動作します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszFilename`  
 インポートするファイルの名前です。  
  
 `pszTargetName`  
 アセンブリにリンクされていると、ファイルの名前を変更するために使用する省略可能な出力ファイル名です。  
  
 `pAssemblyScopeIn`  
 省略可能なスコープ[IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)インターフェイスです。  
  
 `fSmartImport`  
 TRUE の場合、ImportTypes は、それ以外の場合をインポートし、手動で実行する必要があります。  
  
 `pImportToken`  
 ファイルまたはアセンブリの ID を受け取ります。  
  
 `ppAssemblyScope`  
 受信、 [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)インターフェイスです。 ファイルがアセンブリではない場合は NULL です。  
  
 `pdwCountOfScopes`  
 ファイルやインポートのスコープには、検出されたを受け取ります。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は、S_OK を返します。  
  
## <a name="requirements"></a>要件  
 Alink.h が必要です。  
  
## <a name="see-also"></a>関連項目  
 [IALink インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
