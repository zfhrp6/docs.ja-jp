---
title: "System.Uri での International Resource Identifier のサポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# System.Uri での International Resource Identifier のサポート
<xref:System.Uri?displayProperty=fullName> クラスは、国際 Resource Identifier \(IRI\) およびドメイン名国際化 \(IDN\) のサポートが追加されました。  これらの改善は、.NET Framework 3.5、3.0 SP1 と 2.0 SP1 で使用できます。  
  
## IRI と IDN サポート  
 Web アドレスは非常に、一連の文字で構成される Uniform Resource Identifier \(URI\) を使用して通常使用されます:  
  
-   英語のアルファベットの大文字および小文字の ASCII 文字。  
  
-   0 ～ 9 の数字。  
  
-   その他少数の ASCII 記号。  
  
 URI の仕様は、インターネット技術標準化委員会 \(IETF: Internet Engineering Task Force\) から発行された RFC 2396 および RFC 3986 に記述されています。  
  
 インターネットの普及と共に、英語以外の言語を使用してリソースを識別する必要も増えてきました。  このニーズを満たし、かつ非 ASCII 文字 \(Unicode\/ISO 10646 文字セットの文字\) を使用できる識別子に、IRI \(International Resource Identifier\) があります。  IRI の仕様は、IETF から発行された RFC 3987 に記述されています。  IRI を使用すると、URL に Unicode 文字を含めることができます。  
  
 <xref:System.Uri?displayProperty=fullName> の既存のクラスが RFC 3987 に基づいて IRI サポートを提供することによって延期されました。  現在のユーザーには、明確に IRI を有効にしない限り、.NET Framework 2.0 の動作からの変更点は分かりません。  これにより、以前のバージョンの .NET Framework との互換性が確保されます。  
  
 アプリケーションはドメイン名に IRI の分析のルールを適用するかどうかどうかを分析する国際化 \(IDN\) ドメイン名を使用するに適用される、および指定できます。  これは machine.config ファイルまたは app.config ファイルで行うことができます。  
  
 IDN を有効にすると、ドメイン名に含まれるすべての Unicode ラベルが等価の Punycode に変換されます。  Punycode 名は ASCII 文字だけで構成され、必ず xn\-\- というプレフィックスで始まります。  この目的は、インターネット上の既存の DNS サーバーをサポートすることです。ほとんどの DNS サーバーは、ASCII 文字しかサポートしていません \(RFC 3940 を参照\)。  
  
 IRI および IDN を有効にすると、<xref:System.Uri.DnsSafeHost%2A?displayProperty=fullName> プロパティの値に影響します。  IRI および IDN を有効にすると、<xref:System.Uri.Equals%2A?displayProperty=fullName>, <xref:System.Uri.OriginalString%2A?displayProperty=fullName> メソッド、<xref:System.Uri.GetComponents%2A?displayProperty=fullName> メソッド、および <xref:System.Uri.IsWellFormedOriginalString%2A> メソッドの動作が変わる場合もあります。  
  
 <xref:System.GenericUriParser?displayProperty=fullName> クラスも、IRI および IDN をサポートするカスタマイズ可能なパーサーを作成できるように拡張されました。  <xref:System.GenericUriParser?displayProperty=fullName> オブジェクトの動作は、<xref:System.GenericUriParserOptions?displayProperty=fullName> 列挙体で使用可能な値のビットごとの組み合わせを <xref:System.GenericUriParser?displayProperty=fullName> コンストラクターに渡すことによって指定されます。  <xref:System.GenericUriParserOptions?displayProperty=fullName> 型は、このパーサーが、IRI \(International Resource Identifiers\) の RFC 3987 で指定された解析規則をサポートすることを示します。  IRI は、実際に使用されるかを IRI が有効な場合に依存します。  
  
 <xref:System.GenericUriParserOptions?displayProperty=fullName> 型は、このパーサーが、国際化ドメイン名 \(IDN: Internationalized Domain Name\) によるホスト名の解析をサポートしていることを示します。  IDN は、実際に使用されるかを IDN が有効な場合に依存します。  
  
 分析する IRI を有効にすると、RFC 3987 の最新の IRI のルールに従って確認すると文字を正規化します。  既定値が無効になるために分析する IRI の正規化するため、および文字確認が RFC 2396 と 3986 RFC に従って実行されます。  
  
 <xref:System.Uri?displayProperty=fullName> クラスを処理する IRI と IDN は、<xref:System.Configuration.IriParsingElement?displayProperty=fullName> と <xref:System.Configuration.IdnElement?displayProperty=fullName> のコンフィギュレーション設定のクラスを使用して管理されます。  <xref:System.Configuration.IriParsingElement?displayProperty=fullName> の設定により、<xref:System.Uri?displayProperty=fullName> クラスでの IRI 処理が有効または無効になります。  <xref:System.Configuration.IdnElement?displayProperty=fullName> の設定により、<xref:System.Uri> クラスでの IDN 処理が有効または無効になります。  <xref:System.Configuration.IriParsingElement?displayProperty=fullName> の設定も、IDN を間接的に制御します。  IDN 処理を可能にするには、IRI 処理を有効にする必要があります。  IRI 処理が無効な場合、IDN 処理は既定の設定値に設定されるため、互換性のために .NET Framework 2.0 の動作が使用されて、IDN 名は使用されません。  
  
 <xref:System.Configuration.IriParsingElement?displayProperty=fullName> と <xref:System.Configuration.IdnElement?displayProperty=fullName> のコンポーネント クラスのコンフィギュレーション設定が <xref:System.Uri?displayProperty=fullName> の最初のクラスが一度組み立て場合です。  それ以降の構成設定の変更は無視されます。  
  
## 参照  
 <xref:System.Configuration.IdnElement?displayProperty=fullName>   
 <xref:System.Configuration.IriParsingElement?displayProperty=fullName>   
 <xref:System.Uri?displayProperty=fullName>   
 <xref:System.Uri.DnsSafeHost%2A?displayProperty=fullName>