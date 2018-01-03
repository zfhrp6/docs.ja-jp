---
title: "IMetaDataAssemblyEmit::SetAssemblyProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetAssemblyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aab505700b669cae071420117abd71332f49d8b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyProps メソッド
指定された `Assembly` メタデータ構造体を変更します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pma`  
 [in]メタデータ トークンを指定する、`Assembly`メタデータ構造体を変更できます。  
  
 `pbPublicKey`  
 [in]アセンブリの発行者の公開キーへのポインター。  
  
 `cbPublicKey`  
 [in]バイト サイズ`pbPublicKey`です。  
  
 `ulHashAlgId`  
 [in]アセンブリ ファイルのハッシュに使用するハッシュ アルゴリズムの識別子。  
  
 `szName`  
 [in]アセンブリの人間が判読できるテキストの名前。  
  
 `pMetaData`  
 [in]アセンブリのバージョン、プラットフォーム、およびロケールの情報を含む ASSEMBLYMETADATA へのポインター。  
  
 `dwAssemblyFlags`  
 [in]ビットごとの組み合わせ[AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)アセンブリのさまざまな属性を指定する値。  
  
## <a name="remarks"></a>コメント  
 作成する、`Assembly`メタデータ構造体を使用して、 [imetadataassemblyemit::defineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)メソッドです。  
  
## <a name="requirements"></a>必要条件  
 **Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
