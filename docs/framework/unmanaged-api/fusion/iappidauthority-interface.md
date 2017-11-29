---
title: "IAppIdAuthority インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppIdAuthority
api_location: fusion.dll
api_type: COM
f1_keywords: IAppIdAuthority
helpviewer_keywords: IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07bfd26a43d264babc9854b0fd0da909dd329405
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority インターフェイス
メソッドを生成し、アプリケーションの id と参照キーの比較を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|2 つ指定されているかどうかを示す値を取得[IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)インスタンスが等しい。 フラグの値をそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡すことができます。|  
|`IAppIdAuthority::AreReferencesEqual`|2 つ指定されているかどうかを示す値を取得[IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)インスタンスが等しい。 フラグの値をそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡すことができます。|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|2 つの指定した文字列の定義が等しいかどうかを示す値を取得します。 フラグの値をそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡すことができます。|  
|`IAppIdAuthority::AreTextualReferencesEqual`|2 つの指定した文字列参照が等しいかどうかを示す値を取得します。 フラグの値をそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡すことができます。|  
|`IAppIdAuthority::CreateDefinition`|新しく生成されたインターフェイス ポインターを取得`IDefinitionAppId`を現在のスコープ内のアセンブリを表すインスタンス。|  
|`IAppIdAuthority::CreateReference`|新しく作成するインターフェイス ポインターを取得`IReferenceAppId`を表す現在のスコープ内のアセンブリ。|  
|`IAppIdAuthority::DefinitionToText`|指定した文字列形式を取得`IDefinitionAppId`、指定したフラグの値を使用します。|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|示す値を取得するかどうか、指定した`IDefinitionAppId`と`IReferenceAppId`同じアセンブリを表します。|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|指定した定義の文字列と参照文字列が同じアセンブリを表すかどうかを示す値を取得します。|  
|`IAppIdAuthority::GenerateDefinitionKey`|表す、指定した文字列のキーを取得`IDefinitionAppId`インスタンス。|  
|`IAppIdAuthority::GenerateReferenceKey`|表す、指定した文字列のキーを取得`IReferenceAppId`インスタンス。|  
|`IAppIdAuthority::HashDefinition`|指定したハッシュ キーを取得`IDefinitionAppId`インスタンス。|  
|`IAppIdAuthority::HashReference`|指定したハッシュ キーを取得`IReferenceAppId`インスタンス。|  
|`IAppIdAuthority::ReferenceToText`|指定した文字列形式を取得`IReferenceAppId`、指定したフラグの値を使用します。|  
|`IAppIdAuthority::TextToDefinition`|インターフェイス ポインターを取得、`IDefinitionAppId`を指定した文字列キーによって参照されるアセンブリを表すインスタンス。|  
|`IAppIdAuthority::TextToReference`|インターフェイス ポインターを取得、`IReferenceAppId`を指定した文字列キーによって参照されるアセンブリを表すインスタンス。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
