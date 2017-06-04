---
title: "方法 : プライベート フォント コレクションを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "フォント, 作成 (プライベート コレクションを)"
  - "プライベート フォント コレクション, 作成"
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : プライベート フォント コレクションを作成する
<xref:System.Drawing.Text.PrivateFontCollection> クラスは、<xref:System.Drawing.Text.FontCollection> 抽象基本クラスを継承します。  <xref:System.Drawing.Text.PrivateFontCollection> オブジェクトを使用して、アプリケーションに固有のフォント セットを維持できます。  プライベート フォント コレクションには、インストールされているシステム フォントだけでなく、コンピューターにインストールされていないフォントを含むことができます。  プライベート フォント コレクションにフォント ファイルを追加するには、<xref:System.Drawing.Text.PrivateFontCollection> オブジェクトの <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> メソッドを呼び出します。  
  
 <xref:System.Drawing.Text.PrivateFontCollection> オブジェクトの <xref:System.Drawing.Text.FontCollection.Families%2A> プロパティは、<xref:System.Drawing.FontFamily> オブジェクトの配列を格納します。  
  
 プライベート フォント コレクション内のフォント ファミリの数は、そのコレクションに追加されたフォント ファイルの数と必ずしも同じではありません。  たとえば、ArialBd.tff、Times.tff、TimesBd.tff の各ファイルをコレクションに追加するとします。  コレクション内には 3 つのファイルがありますが、Times.tff と TimesBd.tff は同じファミリに属しているため、コレクション内のファミリ数は 2 つだけになります。  
  
## 使用例  
 次の 3 つのフォント ファイルを <xref:System.Drawing.Text.PrivateFontCollection> オブジェクトに追加する例を次に示します。  
  
-   C:\\*systemroot*\\Fonts\\Arial.tff \(Arial、標準\)  
  
-   C:\\*systemroot*\\Fonts\\CourBI.tff \(Courier New、太字斜体\)  
  
-   C:\\*systemroot*\\Fonts\\TimesBd.tff \(Times New Roman、太字\)  
  
 このコードは、<xref:System.Drawing.Text.PrivateFontCollection> オブジェクトの <xref:System.Drawing.Text.FontCollection.Families%2A> プロパティから <xref:System.Drawing.FontFamily> オブジェクトの配列を取得します。  
  
 このコードはコレクション内の <xref:System.Drawing.FontFamily> オブジェクトごとに <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> メソッドを呼び出し、各種のスタイル \(標準、太字、斜体、太字斜体、下線、および取り消し線\) を使用できるかどうかを確認します。  <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> メソッドに渡される引数は、<xref:System.Drawing.FontStyle> 列挙体のメンバーです。  
  
 特定のファミリとスタイルの組み合わせを使用できる場合、<xref:System.Drawing.Font> オブジェクトはそのファミリとスタイルを使用して作成されます。  別の形式の <xref:System.Drawing.Font.%23ctor%2A> コンストラクターの場合、最初に渡される引数は <xref:System.Drawing.FontFamily> オブジェクトですが、この <xref:System.Drawing.Font.%23ctor%2A> コンストラクターに渡される最初の引数はフォント ファミリ名です。  <xref:System.Drawing.Font> オブジェクトが作成されると、そのオブジェクトが <xref:System.Drawing.Graphics> クラスの <xref:System.Drawing.Graphics.DrawString%2A> メソッドに渡され、ファミリ名と一緒にスタイルの名前が表示されます。  
  
 下記のコードによる出力の例を次の図に示します。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")  
  
 次のコード例でプライベート フォント コレクションに追加されている Arial.tff は、Arial 標準スタイルのフォント ファイルです。  しかし、プログラム出力では、Arial フォント ファミリについて標準以外にも使用できるスタイルがいくつか示されています。  これは、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] で、標準スタイルから太字、斜体、および太字斜体の各スタイルをシミュレートできるためです。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では、標準スタイルを基に下線および取り消し線を生成することもできます。  
  
 同様に、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では、太字スタイルまたは斜体スタイルから太字斜体スタイルをシミュレートできます。  プログラム出力には、TimesBd.tff \(Times New Roman 太字\) がコレクション内の唯一の Times ファイルである場合も、Times ファミリの太字斜体スタイルを使用できることが示されます。  
  
 [!code-csharp[System.Drawing.FontsAndText#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  
  
## 参照  
 <xref:System.Drawing.Text.PrivateFontCollection>   
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)