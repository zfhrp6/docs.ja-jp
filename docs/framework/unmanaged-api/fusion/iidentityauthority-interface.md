---
title: IIdentityAuthority インターフェイス
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 692ac4ef4fe8ea64c6a63dc2f02cc04244a842c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432530"
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority インターフェイス
コード オブジェクトの id キーを管理します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|2 つ指定されているかどうかを示す値を取得[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)インスタンスが等しい。|  
|`IIdentityAuthority::AreReferencesEqual`|2 つ指定されているかどうかを示す値を取得[IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)インスタンスが等しい。|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|2 つの指定した文字列の定義 id の形式が等しいかどうかを示す値を取得します。|  
|`IIdentityAuthority::AreTextualReferencesEqual`|2 つの指定した文字列の参照 id の形式が等しいかどうかを示す値を取得します。|  
|`IIdentityAuthority::CreateDefinition`|新しいへのポインターを取得`IDefinitionIdentity`を現在のスコープ内のコード オブジェクトを表すインスタンス。|  
|`IIdentityAuthority::CreateReference`|新しいへのポインターを取得`IReferenceIdentity`を現在のスコープ内のコード オブジェクトを表すインスタンス。|  
|`IIdentityAuthority::DefinitionToText`|指定した書式設定された文字列バージョンを取得`IDefinitionIdentity`です。|  
|`IIdentityAuthority::DefinitionToTextBuffer`|指定した文字列形式を指定したワイド文字バッファーに設定`IDefinitionIdentity`です。|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|示す値を取得するかどうか、指定した`IDefinitionIdentity`と`IReferenceIdentity`インスタンスが同じコード オブジェクトを参照してください。|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|指定した文字列が同じコード オブジェクトを参照するかどうかを示す値を取得します。|  
|`IIdentityAuthority::GenerateDefinitionKey`|指定された文字列を新しく作成されたキーへのポインターを取得`IDefinitionIdentity`です。|  
|`IIdentityAuthority::GenerateReferenceKey`|指定された文字列を新しく作成されたキーへのポインターを取得`IReferenceIdentity`です。|  
|`IIdentityAuthority::HashDefinition`|指定したハッシュ値を取得`IDefinitionIdentity`です。|  
|`IIdentityAuthority::HashReference`|指定したハッシュ値を取得`IreferenceIdentity`です。|  
|`IIdentityAuthority::ReferenceToText`|指定した書式設定された文字列バージョンを取得`IReferenceIdentity`です。|  
|`IIdentityAuthority::ReferenceToTextBuffer`|指定した文字列形式を指定したワイド文字バッファーに設定`IReferenceIdentity`です。|  
|`IIdentityAuthority::TextToDefinition`|インターフェイス ポインターを取得、`IDefinitionIdentity`形式の文字列の指定された対象から生成されたインスタンスです。|  
|`IIdentityAuthority::TextToReference`|インターフェイス ポインターを取得、`IReferenceIdentity`形式の文字列の指定された対象から生成されたインスタンスです。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
