---
title: "Visual Basic でのコンポーネントの作成および使用 | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 1235f62f6ac0878e16387c35150764f3585bc004
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="creating-and-using-components-in-visual-basic"></a>Visual Basic でのコンポーネントの作成および使用
*コンポーネント*は、<xref:System.ComponentModel.IComponent?displayProperty=fullName> インターフェイスを実装するか、<xref:System.ComponentModel.IComponent> を実装するクラスから直接的または間接的に派生するクラスです。 [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)] のコンポーネントは、再利用可能なオブジェクトで、他のオブジェクトとやり取りでき、外部リソースの制御やデザイン時サポートが備わっています。  
  
 コンポーネントの重要な特徴の 1 つは、コンポーネントがデザイン可能であるということです。つまり、コンポーネントであるクラスは [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)] 統合開発環境で使用できます。 コンポーネントは、ツールボックスへの追加、フォームへのドラッグ アンド ドロップ、デザイン サーフェイスでの操作が可能です。 コンポーネントの基本のデザイン時サポートは [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)] に組み込まれているため、コンポーネント開発者は追加の作業を行わずに基本のデザイン時機能を利用できます。  
  
 デザイン可能という点では、"*コントロール*" もコンポーネントに似ています。 ただし、コントロールにはユーザー インターフェイスが用意されているのに対し、コンポーネントには用意されていません。 コントロールは基本コントロール クラスである <xref:System.Windows.Forms.Control> または <xref:System.Web.UI.Control> から派生する必要があります。  
  
## <a name="when-to-create-a-component"></a>コンポーネントを作成する状況  
 デザイン サーフェイス (Windows フォーム デザイナーや Web フォーム デザイナーなど) で使用するクラスにユーザー インターフェイスがない場合、そのクラスは、コンポーネントにして、<xref:System.ComponentModel.IComponent> を実装するか、<xref:System.ComponentModel.IComponent> を直接または間接的に実装するクラスから派生させる必要があります。  
  
 <xref:System.ComponentModel.Component> クラスと <xref:System.ComponentModel.MarshalByValueComponent> クラスは、<xref:System.ComponentModel.IComponent> インターフェイスの基本実装です。 これらのクラスの主な違いは、<xref:System.ComponentModel.Component> クラスは参照渡しでマーシャリングされ、<xref:System.ComponentModel.IComponent> は値渡しでマーシャリングされることにあります。 実装のためのガイドラインを次に示します。  
  
-   コンポーネントを参照渡しでマーシャリングする必要がある場合は、<xref:System.ComponentModel.Component> から派生させます。  
  
-   コンポーネントを値渡しでマーシャリングする必要がある場合は、<xref:System.ComponentModel.MarshalByValueComponent> から派生させます。  
  
-   単一継承が原因でいずれかの基本実装からコンポーネントを派生できない場合は、<xref:System.ComponentModel.IComponent> を実装します。  
  
 デザイン時サポートの詳細については、「[コンポーネントのデザイン時属性](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)」および「[デザイン時サポートの拡張](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)」を参照してください。  
  
## <a name="component-classes"></a>コンポーネントのクラス  
 <xref:System.ComponentModel> 名前空間は、コンポーネントとコントロールの実行時およびデザイン時の動作を実装するために使用できるクラスを提供します。 この名前空間には、属性と型コンバーターの実装、データ ソースへのバインド、コンポーネントのライセンス処理のための基底クラスと基底インターフェイスが含まれています。  
  
 核となるコンポーネント クラスは次のとおりです。  
  
-   <xref:System.ComponentModel.Component>。 <xref:System.ComponentModel.IComponent> インターフェイスの基本実装。 このクラスにより、アプリケーション間でオブジェクトの共有が可能になります。  
  
-   <xref:System.ComponentModel.MarshalByValueComponent>。 <xref:System.ComponentModel.IComponent> インターフェイスの基本実装。  
  
-   <xref:System.ComponentModel.Container>。 <xref:System.ComponentModel.IContainer> インターフェイスの基本実装。 このクラスは、0 個以上のコンポーネントをカプセル化します。  
  
 コンポーネントのライセンス処理に使用するクラスのいくつかを次に示します。  
  
-   <xref:System.ComponentModel.License>。 すべてのライセンスの抽象基底クラスです。 ライセンスは、コンポーネントの特定のインスタンスに付与されます。  
  
-   <xref:System.ComponentModel.LicenseManager>。 コンポーネントにライセンスを追加し、<xref:System.ComponentModel.LicenseProvider> を管理するためのプロパティとメソッドを提供します。  
  
-   <xref:System.ComponentModel.LicenseProvider>。 ライセンス プロバイダーを実装するための抽象基底クラスです。  
  
-   <xref:System.ComponentModel.LicenseProviderAttribute>。 クラスで使用する <xref:System.ComponentModel.LicenseProvider> クラスを指定します。  
  
 コンポーネントの説明や永続化に一般的に使用するクラスを次に示します。  
  
-   <xref:System.ComponentModel.TypeDescriptor>。 属性、プロパティ、イベントなど、コンポーネントの特性に関する情報を提供します。  
  
-   <xref:System.ComponentModel.EventDescriptor>。 イベントに関する情報を提供します。  
  
-   <xref:System.ComponentModel.PropertyDescriptor>。 プロパティに関する情報を提供します。  
  
## <a name="related-sections"></a>関連項目  
 [クラス、コンポーネント、コントロール](http://msdn.microsoft.com/library/db8b842e-44d9-40cc-a0f8-70fd189632c3)  
 "*コンポーネント*" と "*コントロール*" を定義し、それらとクラスの違いについて説明します。  
  
 [コンポーネントの作成](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 コンポーネントの使用を始めるためのロードマップです。  
  
 [コンポーネント作成のチュートリアル](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 コンポーネント プログラミングの詳細な手順について説明するトピックへのリンクを提供します。  
  
 [コンポーネントのクラス](http://msdn.microsoft.com/library/ce2e5647-e673-4c2b-8125-ffebbd9d71bc)  
 クラスをコンポーネントにするために必要な要素、コンポーネントの機能を公開する方法、コンポーネントへのアクセスの制御、コンポーネントのインスタンスの作成方法について説明します。  
  
 [コントロールとコンポーネントの作成時のトラブルシューティング](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 一般的な問題に対処する方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [方法: Windows フォームでデザイン時サポートにアクセスする](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)   
 [方法: デザイン モードでコントロールの外観と動作を拡張する](http://msdn.microsoft.com/library/68f85054-2253-47f5-a4f2-3f1ac8c9f27b)   
 [方法: デザイン モードでコントロールのカスタム初期化を行う](http://msdn.microsoft.com/library/914eaa03-092f-4556-9160-b8a2a40641d9)
