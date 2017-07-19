---
title: "方法 : マネージ HTML DOM (Document Object Model) の要素のスタイルを変更する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "マネージ HTML DOM, 変更 (要素のスタイルを)"
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : マネージ HTML DOM (Document Object Model) の要素のスタイルを変更する
HTML のスタイルを使用してドキュメントの外観と要素を制御できます。  <xref:System.Windows.Forms.HtmlDocument> および <xref:System.Windows.Forms.HtmlElement> は、次の形式のスタイル文字列を設定する <xref:System.Windows.Forms.HtmlElement.Style%2A> プロパティをサポートします。  
  
 `name1:value1;...;nameN:valueN;`  
  
 これは、フォントを Arial に設定し、すべてのテキストを太字に設定するスタイル文字列を持つ `DIV` です。  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 <xref:System.Windows.Forms.HtmlElement.Style%2A> プロパティを使用してスタイルを操作する場合の問題点は、文字列への個々のスタイル設定の追加や削除が面倒なことです。  たとえば、ユーザーがカーソルを `DIV` 上に配置するたびに直前のテキストを斜体で表示し、カーソルを `DIV` から離したときに斜体をオフにする手順は複雑になります。  この方法で多数のスタイルを操作する必要がある場合には、時間が問題になります。  
  
 次のプロシージャには、HTML ドキュメントのスタイルと要素を簡単に操作するために使用できるコードが含まれています。  このプロシージャを実行するには、新しいプロジェクトの作成やフォームへのコントロールの追加など、Windows フォームの基本的なタスクの実行方法を理解している必要があります。  
  
### Windows フォーム アプリケーションのスタイル変更を処理するには  
  
1.  新しい Windows フォーム プロジェクトを作成します。  
  
2.  新しいクラス ファイルを作成します。ファイル名の最後に、プログラミング言語に適した拡張子を付けてください。  
  
3.  このトピックの「例」にある `StyleGenerator` クラス コードをクラス ファイルにコピーし、コードを保存します。  
  
4.  次の HTML を Test.htm という名前のファイルに保存します。  
  
    ```  
    <HTML>  
        <BODY>  
  
            <DIV style="font-face:arial;font-weight:bold;">  
                Hello, world!  
            </DIV><P>  
  
            <DIV>  
                Hello again, world!  
            </DIV><P>  
  
        </BODY>  
    </HTML>  
    ```  
  
5.  `webBrowser1` という名前の <xref:System.Windows.Forms.WebBrowser> コントロールをプロジェクトのメイン フォームに追加します。  
  
6.  プロジェクトのコード ファイルに次のコードを追加します。  
  
    > [!IMPORTANT]
    >  `webBrowser1_DocumentCompleted` イベント ハンドラーが <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> イベントのリスナーとして構成されていることを確認します。  [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] で、<xref:System.Windows.Forms.WebBrowser> コントロールをダブルクリックします。次に、テキスト エディターで、リスナーをプログラムで構成します。  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  プロジェクトを実行します。  カーソルを最初の `DIV` 上に移動して、コードの効果を確認します。  
  
## 使用例  
 `StyleGenerator` クラスの完全なコードを次のコード例に示します。このコードは、既存のスタイル値を解析し、スタイルの追加、変更、および削除をサポートし、変更要求に対応した新しいスタイル値を返します。  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## 参照  
 <xref:System.Windows.Forms.HtmlElement>