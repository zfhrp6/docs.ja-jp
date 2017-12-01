---
title: "外部リソースの解決"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 824a35ee5d4ecafc45167ff3f4bc89802af4ed96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="resolving-external-resources"></a>外部リソースの解決
**XmlResolver**のプロパティ、 **XmlDocument**によって使用される、 **XmlDocument**外部ドキュメント型など、XML データにインラインではないリソースを見つけるためのクラス定義 (Dtd)、エンティティ、およびスキーマです。 これらのリソースは、ネットワーク上やローカル ドライブ上にあり、URI (Uniform Resource Identifier) で識別できます。 これにより、 **XmlDocument**解決するのには**EntityReference**ノードがドキュメント内に存在し、外部の DTD またはスキーマに従ってドキュメントを検証します。  
  
## <a name="fully-trusted-xmldocument"></a>完全に信頼されている XmlDocument  
 **XmlResolver**プロパティの機能に影響、 **XmlDocument.Load**メソッドです。 以下の表方法、 **XmlDocument.XmlResolver**プロパティの動作時に、 **XmlDocument**オブジェクトが完全に信頼されています。 次の表に、 **XmlDocument.Load**メソッドの負荷への入力が、 **TextReader**、**文字列**、**ストリーム**、または**URI**です。 次の表には適用されません、**ロード**メソッド場合、 **XmlDocument**から読み込まれた、 **XmlReader**です。  
  
|XmlResolver プロパティ|関数|メモ|  
|--------------------------|--------------|-----------|  
|プロパティに設定する**XmlResolver**以前に作成を既に設定されているユーザーがプロパティを持つクラス。|**XmlDocument**を使用して、 **XmlResolver** Dtd、エンティティ、およびスキーマなどの外部リソースへの参照を解決するのには、ファイル名を解決するのにを指定します。<br /><br /> **XmlResolver**は追加または内のノードを編集するときに必要な外部のリソースを解決するときにも使用、 **XmlDocument**です。|**XmlResolver**に指定された、 **XmlDocument**外部リソースの検索し、解決に必要なときに使用される競合回避モジュールします。|  
|プロパティに設定**null** (**Nothing** Microsoft Visual Basic .NET で)。|外部のスキーマや DTD の検索など、外部リソースを必要とする機能はサポートされていません。 外部エンティティの解決も行われず、解決が必要なエンティティ ノードの挿入などの編集機能もサポートされません。|**XmlDocument**負荷のファイルを匿名およびその他のリソースを解決するのには行われません。|  
|プロパティが設定されておらず、既定状態のままである。|**XmlUrlResolver**資格情報のインスタンス化されで使用されるで、NULL、 **XmlDocument**外部の Dtd、エンティティ、および、スキーマを検索するファイル名を解決するときに、 **null**ノードの編集時に資格情報が使用されます。||  
  
 次の表に、 **XmlDocument.Load**メソッドとへの入力、**ロード**は、 **XmlReader**と**XmlDocument**は完全に信頼します。  
  
|XmlResolver プロパティ|関数|メモ|  
|--------------------------|--------------|-----------|  
|**XmlResolver**によって使用されるクラス、 **XmlDocument**によって使用されている同じクラスには、 **XmlReader**です。|**XmlDocument**を使用して、 **XmlResolver**に割り当てられた、 **XmlReader**です。<br /><br /> **XmlDocument.Resolver**プロパティに関係なく、設定することはできません、 **XmlDocument**が取得するための信頼レベルを**XmlResolver**から、 **XmlReader**です。 設定をオーバーライドしようとすることはできません、 **XmlReaders**' **XmlResolver**を設定して、 **XmlResolver**のプロパティ、 **XmlDocument**.|**XmlReader**できます、 **XmlTextReader**、 **XmlValidatingReader**、またはカスタム記述リーダー。 使用するリーダーでエンティティ解決がサポートされている場合は、外部エンティティが解決されます。 渡されたリーダーでエンティティ参照がサポートされていない場合は、エンティティ参照は解決されません。|  
  
## <a name="semi-trusted-xmldocument"></a>信頼性の高くない XmlDocument  
 次の表に、どのように**XmlDocument.XmlResolver**プロパティ オブジェクトが信頼度の低い場合の動作です。 このテーブルに適用されます、 **XmlDocument.Load**メソッドの負荷への入力が、 **TextReader**、**文字列**、**ストリーム**、または**URI**です。 次の表には適用されません、**ロード**メソッド場合、 **XmlDocument**から読み込まれた、 **XmlReader**です。  
  
|XmlResolver プロパティ|関数|メモ|  
|--------------------------|--------------|-----------|  
|信頼度の低いシナリオでは、 **XmlResolver**プロパティが null 以外に設定することはできません。|**XmlUrlResolver**で**null**資格情報がインスタンス化されで使用される、 **XmlDocument**外部 Dtd、エンティティを検索するファイル名を解決するときに、スキーマ、および**null**ノードの編集時に資格情報が使用されます。|この動作は、動作と同じ場合に、 **XmlResolver**プロパティが設定されておらず左既定の状態。<br /><br /> **XmlDocument**すべての操作を匿名のアクセス許可を使用します。|  
|プロパティに設定**null** (**Nothing** Microsoft Visual Basic .NET で)。|外部のスキーマや DTD の検索など、外部リソースを必要とする機能はサポートされていません。 外部エンティティの解決も行われず、解決が必要なエンティティ ノードの挿入などの編集機能もサポートされません。|このプロパティが**null**に関係なく場合でも同じの動作は、 **XmlDocument**が完全に信頼されているか、信頼度の低い。|  
|プロパティが設定されておらず、既定状態のままである。|**XmlUrlResolver**で**null**資格情報がインスタンス化されで使用される、 **XmlDocument**外部 Dtd、エンティティを検索するファイル名を解決するときに、スキーマ、および**null**ノードの編集時に資格情報が使用されます。|**XmlDocument**すべての操作を匿名のアクセス許可を使用します。|  
  
 このテーブルに適用されます、 **XmlDocument.Load**メソッドとへの入力、**ロード**は、 **XmlReader**、および**XmlDocument**は信頼度の低い。  
  
|XmlResolver プロパティ|関数|メモ|  
|--------------------------|--------------|-----------|  
|**XmlResolver**によって使用されるクラス、 **XmlDocument**はによって使用されているものと同じ、 **XmlReader**です。|**XmlDocument**を使用して、 **XmlResolver**に割り当てられた、 **XmlReader**です。<br /><br /> **XmlDocument.Resolver**プロパティに関係なく、設定することはできません、 **XmlDocument**が取得するための信頼レベルを**XmlResolver**から、 **XmlReader**です。 設定をオーバーライドしようとすることはできません、 **XmlReaders** **XmlResolver**を設定して、 **XmlResolver**のプロパティ、 **XmlDocument**.|**XmlReader**できます、 **XmlTextReader**検証、 <xref:System.Xml.XmlReader>、またはカスタム記述リーダー。 使用するリーダーでエンティティ解決がサポートされている場合は、外部エンティティが解決されます。 渡されたリーダーでエンティティ参照がサポートされていない場合は、エンティティ参照は解決されません。|  
  
 XmlResolver が正しい資格情報を持つように設定すれば、外部リソースにアクセスできます。  
  
> [!NOTE]
>  取得する方法はありません、 **XmlResolver**プロパティです。 これにより、ユーザーが再利用することを妨げる、 **XmlResolver**資格情報が設定されています。 また場合、 **XmlTextReader**または検証<xref:System.Xml.XmlReader>読み込みに使用された、 **XmlDocument**と**XmlDocument**が設定されているから競合回避モジュール リゾルバーこれらのリーダーがキャッシュされていない、 **XmlDocument**後、**ロード**フェーズ、これも、セキュリティ リスクがあるためです。  
  
 詳細については、<xref:System.Xml.XmlResolver> のリファレンス ページの「解説」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
