    /**
     * 大文字・小文字を無視して2つのリストに共通の要素が存在するかを判定
     * @param sourceList 元のリスト
     * @param targetList 比較対象のリスト
     * @return 共通の要素があれば true、なければ false
     */
    public static boolean containsIgnoreCase(List<String> sourceList, List<String> targetList) {
        if (sourceList == null || targetList == null) {
            return false;
        }

        // targetList を大文字・小文字を無視した Set に変換
        Set<String> targetSet = targetList.stream()
                                          .map(String::toLowerCase)
                                          .collect(Collectors.toSet());

        // sourceList の要素が targetSet に含まれるかを判定
        return sourceList.stream()
                         .map(String::toLowerCase)
                         .anyMatch(targetSet::contains);
    }
}
