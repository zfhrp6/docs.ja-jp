---
title: Serialization1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e63428400a7868b71a2d8e52637e4b22e4c44ee7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="serialization"></a>シリアル化
シリアル化は、オブジェクトを簡単に永続化または転送できる形式に変換するプロセスです。 たとえば、オブジェクトをシリアル化、HTTP を使用して、移行先コンピューターで逆シリアル化した、インターネット経由で転送できます。  
  
 .NET Framework には、さまざまなシリアル化のシナリオ用に最適化された 3 つの主要なシリアル化テクノロジが提供しています。 これらのテクノロジ、およびテクノロジに関連した主な Framework 型を次の表に示します。  
  
|**テクノロジ名**|**メインの種類**|**シナリオ**|  
|-------------------------|--------------------|-------------------|  
|**データ コントラクト シリアル化**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|永続化全般<br />Web サービス<br />JSON|  
|**XML シリアル化**|<xref:System.Xml.Serialization.XmlSerializer>|XML の構造を完全に制御を使用して XML 形式|  
|**ランタイムのシリアル化 (バイナリ、および SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET リモート処理|  
  
 **✓ しないで**新しい型をデザインするときにシリアル化について考えます。  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>サポートする適切なシリアル化テクノロジの選択  
 **✓ を検討してください**データ コントラクト シリアル化をサポートする場合は、型のインスタンスが永続化または Web サービスで使用する必要があります。  
  
 **✓ を検討してください**データ コントラクト シリアル化だけでなく、XML のシリアル化をサポートする場合は、型がシリアル化されるときに生成される XML 形式をより細かく制御する必要があります。  
  
 いくつかの相互運用性、XML を使用する必要があるシナリオの作成でサポートされていないデータ コントラクトのシリアル化、たとえば、XML 属性を生成するために必要な場合があります。  
  
 **✓ を検討してください**ランタイムのシリアル化をサポートする場合は、型のインスタンスは、.NET リモート処理境界を通過する必要があります。  
  
 **避け x**持続性の一般的な理由についてのみランタイムのシリアル化または XML シリアル化をサポートします。 代わりにデータ コントラクト シリアル化してもかまいません。  
  
## <a name="supporting-data-contract-serialization"></a>データ コントラクトのシリアル化のサポート  
 型は、適用することでデータ コントラクト シリアル化をサポートできる、<xref:System.Runtime.Serialization.DataContractAttribute>型に、<xref:System.Runtime.Serialization.DataMemberAttribute>型のメンバー (フィールドとプロパティ) にします。  
  
 **✓ を検討してください**型を部分信頼で使用できる場合、型のパブリック データ メンバーをマークします。  
  
 完全な信頼でデータ コントラクト シリアライザーがシリアル化し、非パブリックの型とメンバーを逆シリアル化が、パブリック メンバーのみをシリアル化および部分的な信頼で逆シリアル化します。  
  
 **✓ しないで**を持つすべてのプロパティの get アクセス操作子および set アクセス操作子を実装する<xref:System.Runtime.Serialization.DataMemberAttribute>です。 データ コントラクト シリアライザーでは、getter と setter のシリアル化可能と見なされる種類の両方が必要です。 (.NET Framework 3.5 SP1 でいくつかのコレクション プロパティできます取得専用)。型を部分信頼で使用しない場合は、1 つまたは両方のプロパティ アクセサーを非パブリックにできます。  
  
 **✓ を検討してください**逆シリアル化されたインスタンスを初期化するためにシリアル化コールバックを使用します。  
  
 オブジェクトの逆シリアル化時にはコンストラクターは呼び出されません。 (ルールの例外があります。 マークされたコンス トラクターのコレクションの<xref:System.Runtime.Serialization.CollectionDataContractAttribute>逆シリアル化中に呼び出されます)。したがって、通常の構築時に実行される任意のロジックは、シリアル化コールバックのいずれかとして実装する必要があります。  
  
 `OnDeserializedAttribute`最もよく使用されるコールバック属性です。 その他の属性には、<xref:System.Runtime.Serialization.OnDeserializingAttribute>、<xref:System.Runtime.Serialization.OnSerializingAttribute>、および <xref:System.Runtime.Serialization.OnSerializedAttribute> があります。 これらを使用して、逆シリアル化前、シリアル化前、およびシリアル化後に実行されるコールバックをマークすることができます。  
  
 **✓ を検討してください**を使用して、<xref:System.Runtime.Serialization.KnownTypeAttribute>を複雑なオブジェクト グラフを逆シリアル化時に使用する必要がありますの具象型を示します。  
  
 **✓ しないで**作成またはシリアル化できる型を変更するときに、上位および下位互換性を検討してください。  
  
 シリアル化した型の将来のバージョンは、現在のバージョンの型に逆シリアル化でき、その逆も可能であることを念頭に置いてください。  
  
 データ メンバー、でもプライベート、内部、変更できないこと、名前、型、または型の将来のバージョンでの順序も、データ コントラクト属性の明示的なパラメーターを使用してコントラクトを保持するために特別な注意を踏まない限りを理解しておいてください。  
  
 シリアル化できる型を変更する場合は、シリアル化との互換性をテストします。 新しいバージョンを古いバージョンに逆シリアル化したり、その逆も試してみてください。  
  
 **✓ を検討してください**実装<xref:System.Runtime.Serialization.IExtensibleDataObject>種類の異なるバージョン間のラウンド トリップを許可します。  
  
 インターフェイスを使用すると、ラウンドトリッピングの間にデータが失われないようにシリアライザーで確認することができます。 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType>を現在のバージョンでは、不明な型の将来のバージョンからデータを格納するプロパティが使用され、そのため、データ メンバーに格納されることはできません。 現在のバージョンは、後でシリアル化すると、将来のバージョンに逆シリアル化、追加のデータができるシリアル化ストリーム。  
  
## <a name="supporting-xml-serialization"></a>XML シリアル化のサポート  
 データ コントラクト シリアル化は、メイン (既定値)、.NET Framework でのシリアル化テクノロジがデータ コントラクト シリアル化をサポートしないシナリオをシリアル化します。 たとえば、シリアライザーによって作成または使用された XML の形状は完全に制御できません。 このような細かい制御が必要な場合は、XML シリアル化を使用するがあり、型は、このシリアル化技術をサポートするために設計する必要があります。  
  
 **避け x**生成される XML の構造を制御する非常に強力な理由がない限り、XML シリアル化を具体的には、型を設計します。 このシリアル化テクノロジは、前のセクションで説明したデータ コントラクトのシリアル化よりも優先されます。  
  
 **✓ を検討してください**を実装する、<xref:System.Xml.Serialization.IXmlSerializable>インターフェイスの XML シリアル化属性を適用することによって提供される内容よりもシリアル化された XML の構造をより詳細に制御する場合。 2 つのメソッド、インターフェイスの<xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>と<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>をシリアル化された XML ストリームを完全に制御できるようにします。 適用することで、型の生成を取得する XML スキーマを制御することも、`XmlSchemaProviderAttribute`です。  
  
## <a name="supporting-runtime-serialization"></a>ランタイム シリアル化のサポート  
 ランタイムのシリアル化は、.NET リモート処理で使用されるテクノロジです。 .NET リモート処理を使用して、型が転送される場合は、ランタイムのシリアル化をサポートするかどうかを確認する必要があります。  
  
 ランタイムのシリアル化の基本的なサポートを適用することで指定することができます、 <xref:System.SerializableAttribute>、単純なランタイムのシリアル化可能なパターンを実装する高度なシナリオが含まれる (実装<xref:System.Runtime.Serialization.ISerializable>シリアル化コンス トラクターを提供)。  
  
 **✓ を検討してください**型が .NET リモート処理で使用する場合は、ランタイムのシリアル化をサポートします。 たとえば、<xref:System.AddIn?displayProperty=nameWithType>名前空間は、.NET リモート処理を使用し、間で交換されるすべての種類`System.AddIn`アドインは、ランタイムのシリアル化をサポートする必要があります。  
  
 **✓ を検討してください**シリアル化プロセスを完全に制御する場合は、ランタイムのシリアル化可能なパターンを実装します。 たとえば、シリアル化または逆シリアル化されたデータを変換したいとします。  
  
 パターンは単純です。 必要な作業は、<xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装し、オブジェクトを逆シリアル化するときに使用する特別なコンストラクターを指定するだけです。  
  
 **✓ しないで**シリアル化コンス トラクターを保護して、型指定された、という名前のサンプルは、ここに示すとおりに正確に 2 つのパラメーターを提供します。  
  
```  
[Serializable]  
public class Person : ISerializable {  
    protected Person(SerializationInfo info, StreamingContext context) {  
        ...  
    }  
}  
```  
  
 **✓ しないで**実装、`ISerializable`メンバー明示的にします。  
  
 **✓ しないで**にリンク確認要求を適用<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType>実装します。 これにより、コアとランタイム シリアライザーは、メンバーにアクセス権を持つのみ完全に信頼できます。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
