---
title: "TableLayoutPanel コントロールの推奨される手順 | Microsoft Docs"
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
  - "サイズの自動調整"
  - "AutoSize プロパティ, TableLayoutPanel コントロール"
  - "推奨される手順, TableLayoutPanel コントロール"
  - "コントロール [Windows フォーム], サイズ変更"
  - "フォーム, 推奨される手順"
  - "レイアウト [Windows フォーム]"
  - "レイアウト [Windows フォーム], 推奨される手順"
  - "レイアウト [Windows フォーム], AutoSize"
  - "サイズ変更, 自動"
  - "TableLayoutPanel コントロール [Windows フォーム], 推奨される手順"
  - "TableLayoutPanel コントロール [Windows フォーム], AutoSize の動作"
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# TableLayoutPanel コントロールの推奨される手順
<xref:System.Windows.Forms.TableLayoutPanel> コントロールが提供する強力なレイアウト機能については、Windows フォームで使用する前に慎重に検討する必要があります。  
  
## 推奨  
 以下の推奨事項は、<xref:System.Windows.Forms.TableLayoutPanel> コントロールを有効に利用する上で役立ちます。  
  
### 対象となるレイアウト  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用する場合は注意が必要です。  サイズ変更が可能なレイアウトが必要であってもすべての状況で使用できるわけではありません。  次のようなレイアウトでは、<xref:System.Windows.Forms.TableLayoutPanel> コントロールの使用が最も適しています。  
  
-   フォームが複数の部分から成り、それぞれを比例的にサイズ変更する必要があるレイアウト。  
  
-   実行時に動的に変更または生成されるレイアウト \(たとえば、ユーザーによるカスタマイズが可能なフィールドが、設定に基づいて追加または削除されるデータ入力フォームなど\)。  
  
-   全体のサイズを固定しておく必要があるレイアウト。  たとえば、ダイアログ ボックスのサイズを 800 × 600 以下に維持しながら、ローカライズされた文字列をサポートする必要がある場合などです。  
  
 次のようなレイアウトでは、<xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用してもあまり有効ではありません。  
  
-   ラベルとテキスト入力領域の列をそれぞれ 1 つずつ持つ単純なデータ入力フォーム。  
  
-   サイズ変更の際に、使用できる領域全体を満たす必要がある 1 つの大きな表示領域を持つフォーム。  この例としては、単一の <xref:System.Windows.Forms.PropertyGrid> コントロールを表示するフォームがあります。  この場合、フォームのサイズを変更したときに他の要素を拡張する必要がないため、固定を適用します。  
  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールに必要なコントロールを慎重に選択します。  アンカーを使用してテキストを 30% まで拡張する余裕がある場合、<xref:System.Windows.Forms.Control.Anchor%2A> プロパティのみを使用することを検討してください。  レイアウトに必要な領域を推定できる場合、<xref:System.Windows.Forms.Control.Dock%2A> と <xref:System.Windows.Forms.Control.Anchor%2A> を使用する方法は、残りの領域と <xref:System.Windows.Forms.Control.AutoSize%2A> 動作の詳細を推定するよりも簡単です。  
  
 一般に、<xref:System.Windows.Forms.TableLayoutPanel> を使用してレイアウトをデザインする場合、デザインはできるだけ単純にします。  
  
### \[ドキュメント アウトライン\] ウィンドウの使用  
 \[ドキュメント アウトライン\] ウィンドウには、レイアウトがツリー ビューに表示されます。コントロールの Z オーダーと親子関係を操作するときに使用できます。  **\[表示\]** メニューの **\[その他のウィンドウ\]** をポイントし、**\[ドキュメント アウトライン\]** をクリックします。  
  
### 入れ子を避ける  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールに他の <xref:System.Windows.Forms.TableLayoutPanel> コントロールを入れ子にするのは避けてください。  入れ子になったレイアウトのデバッグは困難な場合があります。  
  
### ビジュアル継承を避ける  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、Windows フォーム デザイナーのビジュアル継承をサポートしていません。  派生クラスの <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、デザイン時には "ロックされた" 状態で表示されます。  
  
## 参照  
 <xref:System.Windows.Forms.TableLayoutPanel>   
 <xref:System.Windows.Forms.FlowLayoutPanel>