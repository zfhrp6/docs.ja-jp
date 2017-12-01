---
title: "方法 : 分離ストレージでファイルおよびディレクトリを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b8a48473bf9ac91b89657d00d27031255491353
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>方法 : 分離ストレージでファイルおよびディレクトリを作成する
分離ストアを取得した後は、ディレクトリとデータを格納するファイルを作成できます。 ストア内でファイルおよびディレクトリ名は仮想ファイル システムのルートに対して指定します。  
  
 ディレクトリを作成するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType>インスタンス メソッドです。 存在しないディレクトリのサブディレクトリを指定する場合は、両方のディレクトリが作成されます。 既に存在するディレクトリを指定する場合、メソッドは、ディレクトリを作成することがなくを返し、例外はスローされません。 ただし、ディレクトリ名を指定する場合を含む無効な文字を<xref:System.IO.IsolatedStorage.IsolatedStorageException>例外がスローされます。  
  
 ファイルを作成するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType>メソッドです。  
  
 Windows オペレーティング システム、分離ストレージ ファイルおよびディレクトリの名前は区別されません。 つまり、という名前のファイルを作成する場合`ThisFile.txt`、という別のファイルを作成および`THISFILE.TXT`、1 つのファイルを作成します。 ファイル名では、表示目的で元の大文字小文字の区別が保持されます。  
  
## <a name="example"></a>例  
 次のコード例は、分離ストアのファイルとディレクトリを作成する方法を示しています。  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)
