---
title: "IMetaDataImport2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2
helpviewer_keywords: IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1b00879f1d22d49e5f0dc3bdb072e0545feda68d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 インターフェイス
拡張、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)ジェネリック型の使用の機能を提供するインターフェイスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumGenericParamConstraints メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|指定したトークンによって表されるジェネリック パラメーターに関連付けられているジェネリック パラメーターの制約の配列の列挙子を取得します。|  
|[EnumGenericParams メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|トークンのジェネリック パラメーターのトークンが、指定した TypeDef または MethodDef に関連付けられている配列の列挙子を取得します。|  
|[EnumMethodSpecs メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|トークンの MethodSpec トークンが指定した MethodDef または MemberRef に関連付けられている配列の列挙子を取得します。|  
|[GetGenericParamConstraintProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|指定された制約トークンによって表されるジェネリック パラメーターの制約に関連付けられているメタデータを取得します。|  
|[GetGenericParamProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|指定したトークンによって表されるジェネリック パラメーターに関連付けられているメタデータを取得します。|  
|[GetMethodSpecProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|指定した MethodSpec によって参照されるメソッドのメタデータ署名のトークンを取得します。|  
|[GetPEKind メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|ポータブル実行可能 (PE) 内のコードの種類を識別する値ファイルを取得、通常、DLL または EXE ファイルで現在のメタデータ スコープで定義されています。|  
|[GetVersionString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|アセンブリをビルドするために使用されたランタイムのバージョン番号を取得します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection.PortableExecutableKinds>  
 [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
