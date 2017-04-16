---
title: "方法 : クリップボードにデータを追加する | Microsoft Docs"
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
  - "クリップボードのトピック, コピー (データを)"
  - "データ [Windows フォーム], コピー (クリップボードに)"
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : クリップボードにデータを追加する
<xref:System.Windows.Forms.Clipboard> クラスには、Windows オペレーティング システムのクリップボード機能とやり取りするためのメソッドが用意されています。  クリップボードは、データの一時的なレポジトリとして多くのアプリケーションで使用されます。  たとえば、ワード プロセッサは、切り取り、貼り付けの操作でクリップボードを使用します。  クリップボードはデータをアプリケーション間で移動させるときにも使用します。  
  
 データをクリップボードに追加する場合にはデータ形式を指定できるため、別のアプリケーションはその形式を使用できるかどうかを判断できます。  データをさまざまな形式でクリップボードに追加することで、データを使用できるアプリケーションの数を増やすこともできます。  
  
 クリップボード形式は、形式を識別する文字列です。この形式を使用するアプリケーションが、関連データを取得できるようにします。  <xref:System.Windows.Forms.DataFormats> クラスにはユーザーが使用できる定義済みの形式名が含まれています。  また、独自の形式名を使用したり、オブジェクトの型を形式名として使用したりできます。  
  
 1 つまたは複数の形式でデータをクリップボードに追加するには、<xref:System.Windows.Forms.Clipboard.SetDataObject%2A> メソッドを使用します。  このメソッドには任意のオブジェクトを渡すことができますが、データを複数の形式で追加するには、最初に、複数の形式で動作するようにデザインされている個別のオブジェクトにデータを追加する必要があります。  一般には、<xref:System.Windows.Forms.DataObject> にデータを追加しますが、<xref:System.Windows.Forms.IDataObject> インターフェイスを実装している任意の型を使用できます。  
  
 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] では、基本的なクリップボード タスクを簡単に実行できるようにデザインされている新しいメソッドを使って、クリップボードにデータを直接追加できます。  これらのメソッドは、テキストなど、単一の共通形式のデータを操作するときに使用します。  
  
> [!NOTE]
>  Windows ベースのアプリケーションはすべて、クリップボードを共有します。  そのため、別のアプリケーションに切り替えるとクリップボードの内容は変わります。  
>   
>  <xref:System.Windows.Forms.Clipboard> クラスは、シングル スレッド アパートメント \(STA: Single\-Threaded Apartment\) モードに設定されたスレッドでのみ使用できます。  このクラスを使用するには、`Main` メソッドが <xref:System.STAThreadAttribute> 属性でマークされている必要があります。  
>   
>  オブジェクトをクリップボードに置く場合は、オブジェクトをシリアル化する必要があります。  型をシリアル化するには、<xref:System.SerializableAttribute> 属性でマークします。  非シリアル化オブジェクトをクリップボード メソッドに渡すと、例外をスローせずにメソッドは失敗します。  シリアル化の詳細については、「<xref:System.Runtime.Serialization>」を参照してください。  
  
### データを単一の共通形式でクリップボードに追加するには  
  
1.  <xref:System.Windows.Forms.Clipboard.SetAudio%2A>、<xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>、<xref:System.Windows.Forms.Clipboard.SetImage%2A>、または <xref:System.Windows.Forms.Clipboard.SetText%2A> メソッドを使用します。  これらのメソッドは [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 以外では使用できません。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### データをカスタム形式でクリップボードに追加するには  
  
1.  <xref:System.Windows.Forms.Clipboard.SetData%2A> メソッドとカスタム形式名を使用します。  このメソッドは [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 以外では使用できません。  
  
     また、定義済みの形式名を指定して <xref:System.Windows.Forms.Clipboard.SetData%2A> メソッドを使用することもできます。  詳細については、「<xref:System.Windows.Forms.DataFormats>」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### データを複数の形式でクリップボードに追加するには  
  
1.  <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> メソッドを使用し、データを格納している <xref:System.Windows.Forms.DataObject> を渡します。  [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] よりも前のバージョンでクリップボードにデータを追加する場合は、このメソッドを使う必要があります。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## 参照  
 [ドラッグ アンド ドロップ操作とクリップボードのサポート](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)   
 [方法 : クリップボードからデータを取得する](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)