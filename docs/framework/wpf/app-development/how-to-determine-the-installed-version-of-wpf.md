---
title: '方法: インストールされている WPF のバージョンを確認する'
ms.date: 03/30/2017
helpviewer_keywords:
- version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
ms.openlocfilehash: c59fa0d0a4d94c6e6a2ab72a4cd7a3c066649fb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545852"
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a>方法: インストールされている WPF のバージョンを確認する
現在インストールされているバージョンのバージョン番号[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]内にある、**レジストリ**です。  
  
 バージョン番号を検索するには。  
  
1.  **[スタート]** メニューで、 **[ファイル名を指定して実行]** をクリックします。  
  
2.  **開く**、型**regedit.exe**です。  
  
3.  次のキーを開きます。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]にバージョン番号が格納されている、**バージョン**値。
