---
title: "IMetaDataAssemblyImport::FindAssembliesByName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindAssembliesByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3b957430e66e4381a9be33ceb687d7aecba53a4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName メソッド
指定したアセンブリの配列を取得`szAssemblyName`参照の解決には、共通言語ランタイム (CLR) で使用されている標準的な規則を使用して、パラメーター。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,   
    [in]  LPCWSTR     szPrivateBin,   
    [in]  LPCWSTR     szAssemblyName,   
    [out] IUnknown    *ppIUnk[],   
    [in]  ULONG       cMax,   
    [out] ULONG       *pcAssemblies  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szAppBase`  
 [in]指定されたアセンブリを検索するためのルート ディレクトリ。 この値に設定されている場合`null`、`FindAssembliesByName`はグローバル アセンブリ キャッシュでのみアセンブリを検索します。  
  
 `szPrivateBin`  
 [in]セミコロンで区切られたサブディレクトリ (たとえば、「bin; bin2」)、アセンブリを検索するためのルート ディレクトリの下の一覧。 既定の調査規則で指定されているだけでなく、これらのディレクトリがプローブされます。  
  
 `szAssemblyName`  
 [in]検索対象のアセンブリの名前。 この文字列の形式が、クラスのリファレンス ページで定義されている<xref:System.Reflection.AssemblyName>です。  
  
 `ppIUnk`  
 [in]型の配列 <<!--zzxref:IUnknown --> `IUnknown`> に配置するための`IMetadataAssemblyImport`インターフェイス ポインター。  
  
 `cMax`  
 [out]配置できるインターフェイス ポインターの最大数`ppIUnk`です。  
  
 `pcAssemblies`  
 [out]インターフェイス ポインターの数が返されます。 つまり、インターフェイス ポインターの数が実際に配置`ppIUnk`です。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`正常に返されます。|  
|`S_FALSE`|アセンブリは存在しません。|  
  
## <a name="remarks"></a>コメント  
 アセンブリ名、付与、`FindAssembliesByName`メソッドは、次のアセンブリ参照を解決するための標準の規則を使用してアセンブリを検索します。 (詳細については、次を参照してください[ランタイムがアセンブリを検索する方法](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。)。`FindAssembliesByName`により、呼び出し元アセンブリの競合回避モジュール コンテキストのアプリケーション ベースで、プライベート検索パスなどのさまざまな側面を構成します。  
  
 `FindAssembliesByName`メソッドが、CLR アセンブリ解決ロジックを実行するために、プロセスで初期化する必要があります。 そのため、呼び出す必要があります[CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (COINITEE_DEFAULT を渡す) 呼び出しの前に`FindAssembliesByName`、して次の呼び出しを[CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)です。  
  
 `FindAssembliesByName`返します、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)に渡される、アセンブリ名のアセンブリ マニフェストを含むファイルへのポインター。 (たとえば、バージョンが含まれていない場合) 特定のアセンブリ名が完全に指定されていない場合は、複数のアセンブリを返される可能性があります。  
  
 `FindAssembliesByName`コンパイル時参照アセンブリを検索しようとするコンパイラで通常使用されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ランタイムがアセンブリを検索する方法](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
