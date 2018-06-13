---
title: '方法 : C# のアプリケーションに複数の設定セットを追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 029dffc878c62613e291620a2bd86971f369d15a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520810"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>方法 : C# のアプリケーションに複数の設定セットを追加する #
場合によってで、アプリケーションに複数セットの設定があることができます。 たとえばを開発しているアプリケーションの設定の特定のグループが頻繁に変更すると思われる場合だと考えられますファイルを置換できる、されるように 1 つのファイルに分離してその他の設定は変わりません。 Visual Studio では、複数のセットの設定をプロジェクトに追加することができます。 設定の追加セットは、Properties.Settings オブジェクト経由でアクセスできます。  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>アプリケーションに追加の設定セットを追加するには  
  
1.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 **[新しい項目の追加]** ダイアログ ボックスが開きます。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、**設定ファイル**、ファイルの名前を入力して、をクリックして**追加**をソリューションに新しい設定ファイルを追加します。  
  
3.  **ソリューション エクスプ ローラー**に、新しい設定ファイルをドラッグして、**プロパティ**フォルダーです。 これにより、コードで使用できる新しい設定です。  
  
4.  追加し、その他の設定ファイルと同様に、このファイルの設定を使用します。 この設定は、Properties.Settings オブジェクトでのグループにアクセスできます。  
  
## <a name="see-also"></a>関連項目  
 [アプリケーション設定とユーザー設定の使用](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
