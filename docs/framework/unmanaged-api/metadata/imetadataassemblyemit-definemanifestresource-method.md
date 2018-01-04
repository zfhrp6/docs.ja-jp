---
title: "IMetaDataAssemblyEmit::DefineManifestResource メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineManifestResource
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a435c946e13950faad7545e3da78ce373ee7fa0d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource メソッド
指定したマニフェスト リソースのメタデータを含む `ManifestResource` 構造体を作成し、関連付けられたメタデータ トークンを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szName`  
 [in]リソースの名前。  
  
 `tkImplementation`  
 [in]型のメタデータ トークン`mdtFile`または`mdtAssemblyRef`リソース プロバイダーにマップします。 NULL 値のメタデータが埋め込まれているファイルが、リソース プロバイダーであることを示します。  
  
 `dwOffset`  
 [in]ファイル内のリソースの先頭までのオフセット。 スタンドアロン ファイル内のリソースのこの常に 0 になります。 PE (ポータブル実行可能) ファイルには、リソースが埋め込まれている場合はリソース cor.h ヘッダー ファイルで指定された位置から開始する BLOB のオフセットです。  
  
 `dwResourceFlags`  
 [in]リソース定義のプロパティ設定を指定するフラグ値のビットごとの組み合わせ。  
  
 `pmdmr`  
 [out]返されるメタデータ トークンへのポインター。  
  
## <a name="remarks"></a>コメント  
 1 つ`ManifestResource`の各アセンブリのファイルで実装されている各リソースのメタデータ構造体を定義する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
