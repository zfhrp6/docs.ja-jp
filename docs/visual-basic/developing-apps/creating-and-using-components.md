---
title: "Creating and Using Components in Visual Basic | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "components [Visual Basic]"
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Creating and Using Components in Visual Basic
[!INCLUDE[vs2017banner](../../visual-basic/developing-apps/includes/vs2017banner.md)]

*コンポーネント*とは、<xref:System.ComponentModel.IComponent?displayProperty=fullName> インターフェイスを実装するクラス、または <xref:System.ComponentModel.IComponent> を実装するクラスから直接または間接的に派生されたクラスです。  [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort-md.md)] のコンポーネントは、再利用可能なオブジェクトで、他のオブジェクトとやり取りでき、外部リソースの制御やデザイン時サポートが備わっています。  
  
 コンポーネントの重要な特徴の 1 つが、コンポーネントはデザイン可能だということです。つまり、コンポーネントであるクラスは [!INCLUDE[vsprvs](../../csharp/includes/vsprvs-md.md)] 統合開発環境で使用できます。  コンポーネントは、ツールボックスへの追加、フォームへのドラッグ アンド ドロップ、およびデザイン サーフェイスでの操作が可能です。  コンポーネントのデザイン時サポートは [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort-md.md)] に組み込まれているため、コンポーネント開発者は追加の作業を行わずに基本のデザイン時機能を利用できます。  
  
 デザイン可能という点では、*コントロール* もコンポーネントに似ています。  しかし、コントロールはユーザー インターフェイスを持つのに対し、コンポーネントは持ちません。  コントロールは、<xref:System.Windows.Forms.Control> または <xref:System.Web.UI.Control> のいずれかの基本コントロール クラスを派生する必要があります。  
  
## コンポーネントの作成が必要な状況  
 デザイン サーフェイス \(Windows フォーム デザイナー、Web フォーム デザイナーなど\) で使用するクラスがユーザー インターフェイスを持たない場合は、そのクラスはコンポーネントにする必要があり、<xref:System.ComponentModel.IComponent> を実装するか、または <xref:System.ComponentModel.IComponent> を直接または間接的に実装するクラスから派生させます。  
  
 <xref:System.ComponentModel.Component> クラスおよび <xref:System.ComponentModel.MarshalByValueComponent> クラスは <xref:System.ComponentModel.IComponent> インターフェイスの基本実装です。  両クラスの主要な違いは、<xref:System.ComponentModel.Component> クラスは参照渡しでマーシャリングされるのに対し、<xref:System.ComponentModel.IComponent> は値渡しでマーシャリングされるということです。  実装のためのガイドラインを次に示します。  
  
-   コンポーネントを参照渡しでマーシャリングする必要がある場合には、<xref:System.ComponentModel.Component> から派生します。  
  
-   コンポーネントを値渡しでマーシャリングする必要がある場合には、<xref:System.ComponentModel.MarshalByValueComponent> から派生します。  
  
-   単一継承のためにいずれかの基本実装からコンポーネントを派生できない場合には、<xref:System.ComponentModel.IComponent> を実装します。  
  
 デザイン時サポートの詳細については、「[コンポーネントのデザイン時属性](../Topic/Design-Time%20Attributes%20for%20Components.md)」および「[Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)」を参照してください。  
  
## コンポーネントのクラス  
 <xref:System.ComponentModel> 名前空間には、コンポーネントやコントロールの実行時動作およびデザイン時動作を実装するためのクラスが用意されています。  この名前空間には、属性、型コンバーター、データ ソースへの連結、およびライセンス コンポーネントを実装するための基本クラスと基本インターフェイスが含まれています。  
  
 中心となるコンポーネント クラスを以下に示します。  
  
-   <xref:System.ComponentModel.Component>.  <xref:System.ComponentModel.IComponent> インターフェイスの基本実装です。  このクラスによりアプリケーション間でオブジェクトを共有できるようになります。  
  
-   <xref:System.ComponentModel.MarshalByValueComponent>.  <xref:System.ComponentModel.IComponent> インターフェイスの基本実装です。  
  
-   <xref:System.ComponentModel.Container>.  <xref:System.ComponentModel.IContainer> インターフェイスの基本実装です。  このクラスは、いくつかのコンポーネントをカプセル化します \(コンポーネントがない場合もあります\)。  
  
 コンポーネントのライセンス処理に使用する主なクラスを以下に示します。  
  
-   <xref:System.ComponentModel.License>.  すべてのライセンスの抽象基本クラスです。  ライセンスは、コンポーネントの特定のインスタンスに対して付与されます。  
  
-   <xref:System.ComponentModel.LicenseManager>.  コンポーネントにライセンスを与え、<xref:System.ComponentModel.LicenseProvider> を管理するためのプロパティとメソッドを提供します。  
  
-   <xref:System.ComponentModel.LicenseProvider>.  ライセンス プロバイダーを実装するための抽象基本クラスです。  
  
-   <xref:System.ComponentModel.LicenseProviderAttribute>.  クラスと一緒に使用する <xref:System.ComponentModel.LicenseProvider> クラスを指定します。  
  
 コンポーネントの説明や永続化に一般的に使用するクラスを以下に示します。  
  
-   <xref:System.ComponentModel.TypeDescriptor>.  属性、プロパティ、イベントなど、コンポーネントの特性に関する情報を提供します。  
  
-   <xref:System.ComponentModel.EventDescriptor>.  イベントに関する情報を提供します。  
  
-   <xref:System.ComponentModel.PropertyDescriptor>.  プロパティについての情報を提供します。  
  
## 関連項目  
 [クラス、コンポーネント、コントロール](../Topic/Class%20vs.%20Component%20vs.%20Control.md)  
 *コンポーネント*と*コントロール*の定義を示し、それらとクラスの違いについて説明します。  
  
 [コンポーネントの作成](../Topic/Component%20Authoring.md)  
 コンポーネントの使用を始めるためのロードマップです。  
  
 [Component Authoring Walkthroughs](../Topic/Component%20Authoring%20Walkthroughs.md)  
 コンポーネント プログラミングの詳細な手順について説明するトピックにリンクします。  
  
 [コンポーネントのクラス](../Topic/Component%20Classes.md)  
 クラスがコンポーネントになるために必要な要素、コンポーネントの機能を公開する方法、コンポーネントへのアクセスを制御する方法、およびコンポーネントのインスタンスをどのように作成するかを制御する方法について説明します。  
  
 [コントロールとコンポーネントの作成時のトラブルシューティング](../Topic/Troubleshooting%20Control%20and%20Component%20Authoring.md)  
 一般的な問題に対処する方法について説明します。  
  
## 参照  
 [How to: Access Design\-Time Support in Windows Forms](../Topic/How%20to:%20Access%20Design-Time%20Support%20in%20Windows%20Forms.md)   
 [How to: Extend the Appearance and Behavior of Controls in Design Mode](../Topic/How%20to:%20Extend%20the%20Appearance%20and%20Behavior%20of%20Controls%20in%20Design%20Mode.md)   
 [How to: Perform Custom Initialization for Controls in Design Mode](../Topic/How%20to:%20Perform%20Custom%20Initialization%20for%20Controls%20in%20Design%20Mode.md)