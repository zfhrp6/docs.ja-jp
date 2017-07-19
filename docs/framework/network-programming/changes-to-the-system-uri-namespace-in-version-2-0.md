---
title: "バージョン 2.0 での System.Uri 名前空間の変更 | Microsoft Docs"
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
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# バージョン 2.0 での System.Uri 名前空間の変更
<xref:System.Uri?displayProperty=fullName> クラスに複数の変更が行われています。  これらの変更は、間違った態度、拡張有用性およびセキュリティを強化フィックス。  
  
## 古いおよび使用されていないメンバ  
 :コンストラクター  
  
-   `dontEscape`パラメータがあるすべてのコンストラクター。  
  
 方法:  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## 変更  
  
-   クエリの品目が ftp ファイル \(、など\) に慣れているない URI の設定「または" 行が、<xref:System.Uri.Query%2A> の一部の先頭に常に脱出し、には考慮されません。  
  
-   暗黙ファイルの URI \("C:\\directory\\file@name.txt"\) の、フラグメント文字 \('\#'\) は完全に unescaping 要求するまたは <xref:System.Uri.LocalPath%2A> です `true`常にします脱出 。  
  
-   ホストネーム UNC のサポートが削除されました。; 国際ホストネームを表すための IDN の仕様は採用されました。  
  
-   <xref:System.Uri.LocalPath%2A> は完全に unescaped 文字列を常に返します。  
  
-   <xref:System.Uri.ToString%2A> するには脱出「」、「unescape か。」、「\#」文字。  
  
-   <xref:System.Uri.Equals%2A> は平等の小切手と終了 <xref:System.Uri.Query%2A> の一部が含まれます。  
  
-   オペレータ「」および「\! \=\=\=」上書きされ、<xref:System.Uri.Equals%2A> 方法をにリンク。  
  
-   <xref:System.Uri.IsLoopback%2A> は、一貫した結果を少し異なります。  
  
-   `file:///path`URI 「file:\/\/path」」と「に、変換されません。  
  
-   」終了「&#124; ホスト名のターミネーターとして認識されます。  つまり、「http:\/\/consoto.com\#fragment」http:\/\/contoso.com\/\#fragment」と「に変換されます。  
  
-   基準を URI 片と組み合わせるフィックスときにバグ。  
  
-   <xref:System.Uri.HostNameType%2A> のバグはフィックス。  
  
-   分析する NNTP のバグはフィックス。  
  
-   フォームの URI HTTP:contoso.com は、分析の例外を投げます。  
  
-   フレームワークが正しく URI の userinfo を処理します。  
  
-   URI のパス圧縮は URI の内訳がルート上のファイル システムをスキャンするようにフィックス。  
  
## 参照  
 <xref:System.Uri?displayProperty=fullName>