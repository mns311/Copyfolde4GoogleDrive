function copyCurrentFolderToMyDrive() {
    // 現在のスクリプトが保存されているフォルダを取得
    var currentFileId = ScriptApp.getScriptId(); // 現在のスクリプトの ID
    var currentFolder = DriveApp.getFileById(currentFileId).getParents().next();

    // コピー先（マイドライブ）を取得
    var destinationFolder = DriveApp.getRootFolder();

    // フォルダのコピーを開始
    try {
        var copiedFolder = destinationFolder.createFolder(currentFolder.getName() + "_コピー");
        copyFolderContentsWithAPI(currentFolder, copiedFolder, currentFileId);
        Logger.log("フォルダをコピーしました: " + copiedFolder.getName());
    } catch (e) {
        Logger.log("エラーが発生しました: " + e.message);
    }
}

// フォルダ内のすべての内容（GAS ファイル対応）を再帰的にコピー
function copyFolderContentsWithAPI(sourceFolder, destinationFolder, currentFileId) {
    var files = sourceFolder.getFiles();
    while (files.hasNext()) {
        var file = files.next();
        try {
            if (file.getMimeType() === MimeType.GOOGLE_APPS_SCRIPT) {
                if (file.getId() !== currentFileId) {
                    // GAS ファイルをコピー
                    var copiedScriptFile = Drive.Files.copy({}, file.getId());
                    var copiedFile = DriveApp.getFileById(copiedScriptFile.id);
                    copiedFile.setName(file.getName()); // 名前を元に戻す
                    copiedFile.moveTo(destinationFolder);
                }
            } else {
                // 通常ファイルをコピー
                file.makeCopy(file.getName(), destinationFolder);
            }
        } catch (e) {
            Logger.log("ファイルのコピー中にエラーが発生しました: " + file.getName() + " - " + e.message);
        }
    }

    // サブフォルダのコピー
    var subFolders = sourceFolder.getFolders();
    while (subFolders.hasNext()) {
        var subFolder = subFolders.next();
        try {
            var newSubFolder = destinationFolder.createFolder(subFolder.getName());
            copyFolderContentsWithAPI(subFolder, newSubFolder, currentFileId);
        } catch (e) {
            Logger.log("サブフォルダのコピー中にエラーが発生しました: " + subFolder.getName() + " - " + e.message);
        }
    }
}
