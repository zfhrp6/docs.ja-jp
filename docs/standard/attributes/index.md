---
title: "属性を使用したメタデータの拡張 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "注釈を付ける (プログラミング要素に)"
  - "属性 [.NET Framework], メタデータ"
  - "共通言語ランタイム, 属性"
  - "要素 [.NET Framework], 属性"
  - "拡張 (メタデータを)"
  - "キーワードに似た記述的な宣言"
  - "メタデータ, 拡張"
  - "ランタイム, 属性"
ms.assetid: 30386922-1e00-4602-9ebf-526b271a8b87
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 属性を使用したメタデータの拡張
共通言語ランタイムでは、属性と呼ばれるキーワードに似た記述的な宣言を追加して、型、フィールド、メソッド、プロパティなどのプログラミング要素に注釈を付けることができます。  ランタイム用にコードをコンパイルすると、コードは Microsoft Intermediate Language \(MSIL\) に変換され、コンパイラによって生成されるメタデータと共に、ポータブル実行可能 \(PE\) ファイルに格納されます。  属性を使用すると、ランタイム リフレクション サービスで抽出できる記述的な情報をメタデータに追加できます。  属性は、<xref:System.Attribute?displayProperty=fullName> から派生する特殊なクラスのインスタンスを宣言するときに、コンパイラによって作成されます。  
  
 .NET Framework では、属性がさまざまな理由と目的で使用されます。  属性を使用して、データをシリアル化する方法を記述したり、セキュリティの適用に使用する特性を指定したりします。また、コードをデバッグしやすい状態に保つためにジャスト イン タイム \(JIT\) コンパイラによる最適化を制限する場合も、属性を使用します。  さらに、ファイル名やコードの作成者の記録、およびフォームの開発時にコントロールやメンバーを表示するかどうかの制御も、属性で指定します。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[属性の適用](../../../docs/standard/attributes/applying-attributes.md)|コードの要素に属性を適用する方法を説明します。|  
|[カスタム属性の記述](../../../docs/standard/attributes/writing-custom-attributes.md)|カスタム属性クラスをデザインする方法を説明します。|  
|[属性に格納されている情報の取得](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|実行コンテキストに読み込まれるコードのカスタム属性を取得する方法を説明します。|  
|[メタデータと自己言及的なコンポーネント](../../../docs/standard/metadata-and-self-describing-components.md)|メタデータの概要と、.NET Framework のポータブル実行可能 \(PE\) ファイル内でメタデータがどのように実装されるかを説明します。|  
|[方法 : リフレクションのみのコンテキストにアセンブリを読み込む](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|リフレクションのみのコンテキストでカスタム属性情報を取得する方法を説明します。|  
  
## 参照  
 <xref:System.Attribute?displayProperty=fullName>