---
title: "方法 : クリップボードからデータを取得する | Microsoft Docs"
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
  - "クリップボードのトピック, 取得 (データを)"
  - "貼り付け (クリップボード データを)"
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : クリップボードからデータを取得する
<xref:System.Windows.Forms.Clipboard> クラスには、Windows オペレーティング システムのクリップボード機能とやり取りするためのメソッドが用意されています。  クリップボードは、データの一時的なレポジトリとして多くのアプリケーションで使用されます。  たとえば、ワード プロセッサは、切り取り、貼り付けの操作でクリップボードを使用します。  クリップボードはデータをアプリケーション間で移動させるときにも使用します。  
  
 アプリケーションによっては、データが複数の形式でクリップボードに格納される場合もあります。そうすることで、より多くのアプリケーションがデータを使用できるからです。  クリップボードの形式は、その形式を識別する文字列です。  識別された形式を使用するアプリケーションでは、クリップボード上の関連データを取得できます。  <xref:System.Windows.Forms.DataFormats> クラスにはユーザーが使用できる定義済みの形式名が含まれています。  また、独自の形式名を使用したり、オブジェクトの型を形式名として使用したりできます。  データをクリップボードに追加する方法については、「[方法 : クリップボードにデータを追加する](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)」を参照してください。  
  
 特定の形式のデータがクリップボードに含まれているかどうかを調べるには、いずれかの `Contains`*Format* メソッドを使用するか、または <xref:System.Windows.Forms.Clipboard.GetData%2A> メソッドを使用します。  クリップボードからデータを取得するには、いずれかの `Get`*Format* メソッドを使用するか、<xref:System.Windows.Forms.Clipboard.GetData%2A> メソッドを使用します。  これらは、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] で新しく追加されたメソッドです。  
  
 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] よりも前のバージョンを使用してクリップボードのデータにアクセスする場合は、<xref:System.Windows.Forms.Clipboard.GetDataObject%2A> メソッドを使用し、返された <xref:System.Windows.Forms.IDataObject> のメソッドを呼び出します。  返されたオブジェクト内で特定の形式が利用可能かどうかを調べるには、たとえば <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> メソッドを呼び出します。  
  
> [!NOTE]
>  Windows ベースのアプリケーションはすべて、システムのクリップボードを共有します。  そのため、別のアプリケーションに切り替えるとクリップボードの内容は変わります。  
>   
>  <xref:System.Windows.Forms.Clipboard> クラスは、シングル スレッド アパートメント \(STA: Single\-Threaded Apartment\) モードに設定されたスレッドでのみ使用できます。  このクラスを使用する前に、`Main` メソッドが <xref:System.STAThreadAttribute> 属性でマーク付けされていることを確認してください。  
  
### クリップボードからデータを単一の一般的な形式で取得するには  
  
1.  <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>、<xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>、<xref:System.Windows.Forms.Clipboard.GetImage%2A>、または <xref:System.Windows.Forms.Clipboard.GetText%2A> メソッドを使用します。  必要に応じて、最初に対応する `Contains`*Format* のメソッドを使用して、データが特定の形式で利用可能かどうかを判断することもできます。  これらのメソッドは [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 以外では使用できません。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### クリップボードからデータをカスタム形式で取得するには  
  
1.  <xref:System.Windows.Forms.Clipboard.GetData%2A> メソッドとカスタム形式名を使用します。  このメソッドは [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 以外では使用できません。  
  
     また、定義済みの形式名を指定して <xref:System.Windows.Forms.Clipboard.SetData%2A> メソッドを使用することもできます。  詳細については、「<xref:System.Windows.Forms.DataFormats>」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### クリップボードからデータを複数の形式で取得するには  
  
1.  <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> メソッドを使用してください。  [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] よりも前のバージョンでクリップボードからデータを取得する場合は、このメソッドを使う必要があります。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## 参照  
 [ドラッグ アンド ドロップ操作とクリップボードのサポート](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)   
 [方法 : クリップボードにデータを追加する](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)