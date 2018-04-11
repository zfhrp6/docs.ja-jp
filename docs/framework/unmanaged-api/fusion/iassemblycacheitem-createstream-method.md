---
title: IAssemblyCacheItem::CreateStream メソッド
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAsssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 726efe69f67627c48108b6b1ece9fe52f34a91c1
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2018
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream メソッド
指定した名前と形式を使用するストリームを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateStream (  
    [in]  DWORD dwFlags,  
    [in]  LPCWSTR pszStreamName,  
    [in]  DWORD dwFormat,  
    [in]  DWORD dwFormatFlags,  
    [out] IStream **ppIStream,  
    [in, optional] ULARGE_INTEGER *puliMaxSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFlags`  
 [in]ものがありますで定義されているフラグです。  
  
 `pszStreamName`  
 [in]作成されるストリームの名前。  
  
 `dwFormat`  
 [in]ストリーミングするファイルの形式です。  
  
 `dwFormatFlags`  
 [in]ファイル形式に固有のものがありますで定義されているフラグです。  
  
 `ppIStream`  
 [out]返されたのアドレスへのポインター [IStream](https://msdn.microsoft.com/library/aa380034.aspx)インスタンス。  
  
 `puliMaxSize`  
 [in、省略可能]によって参照されるストリームの最大サイズ`ppIStream`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Fusion.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IAssemblyCacheItem インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
