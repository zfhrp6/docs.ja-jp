---
title: CallbackBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9df9629e280a2aec6acf93773e09384e763280ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="callbackbehavior"></a>CallbackBehavior
CallbackBehavior  
  
## <a name="syntax"></a>構文  
  
```  
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>メソッド  
 CallbackBehavior クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 CallbackBehavior クラスには、次のプロパティがあります。  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 true の場合、サービスが双方向セッションを閉じると、セッションが自動的に閉じられます。  
  
### <a name="concurrencymode"></a>ConcurrencyMode  
 データ型: string  
アクセスの種類 : 読み取り専用  
  
 サービスが単一のスレッド、複数のスレッド、再入可能呼び出しのいずれをサポートするかを指定します。  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 不明なシリアル化データをネットワークで送信するかどうかを指定する値です。  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 有効にした場合は、コールバックの例外に関する詳細情報が、サービスに戻されるエラーに添付されます。  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 1 つのシリアル化されたオブジェクトで許可される項目の最大数。  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 現在の同期コンテキストを使用して実行のスレッドを選択するかどうかを指定します。  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 システムまたはアプリケーションで SOAP MustUnderstand ヘッダー処理を強制的に行うかどうかを指定します。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
