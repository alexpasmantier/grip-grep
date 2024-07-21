
# Grab

A faster, more lightweight, ripgrep alternative.

## Installation
### Using Cargo
```bash
$ cargo install grab
```

## Usage
```sh
$ grab "some\s+pattern" .

/somewhere/grab/src/cli.rs
9: pub struct Cli {
11:     pub pattern: String,
14:     pub path: PathBuf,
18:     pub ignore_paths: Vec<PathBuf>,
22:     pub respect_gitignore: bool,
26:     pub max_results: usize,
30:     pub n_threads: usize,
34:     pub multiline: bool,
38:     pub json: bool,
42:     pub file_paths_only: bool,
46: pub struct PostProcessedCli {
47:     pub pattern: String,
48:     pub path: PathBuf,
49:     pub ignored_paths: Vec<PathBuf>,
50:     pub max_results: usize,
51:     pub n_threads: usize,
52:     pub respect_gitignore: bool,
53:     pub multiline: bool,
54:     pub print_mode: PrintMode,
57: pub fn process_cli_args(cli: Cli) -> anyhow::Result<PostProcessedCli> {

/somewhere/grab/src/utils.rs
3: pub fn resolve_paths(paths: Vec<PathBuf>) -> Vec<PathBuf> {
7: pub fn resolve_path(path: PathBuf) -> PathBuf {

/somewhere/grab/src/search.rs
12: pub struct SearchResult {
13:     pub line_number: u64,
14:     pub line: String,
18: pub struct FileResults {
19:     pub path: PathBuf,
20:     pub results: Vec<SearchResult>,
34:     pub fn is_empty(&self) -> bool {
38:     pub fn len(&self) -> usize {
52: pub fn search_file<'a>(
82: pub fn build_matcher(pattern: &str) -> anyhow::Result<RegexMatcher> {
87: pub fn build_searcher(multiline: bool) -> Searcher {

/somewhere/grab/src/fs.rs
5: pub fn walk_builder(

/somewhere/grab/src/main.rs
17: pub fn main() -> anyhow::Result<()> {

/somewhere/grab/src/printer.rs
6: pub enum PrintMode {
12: pub struct Printer {
18:     pub fn new(mode: PrintMode) -> Printer {
27:     pub fn write(&mut self, results: FileResults) -> Result<()> {
39:     pub fn print(&mut self) -> Result<()> {

```

## Documentation
```sh
$ grab --help
```

```plaintext
A faster, more lightweight, ripgrep alternative.

Usage: grab [OPTIONS] <PATTERN> <PATH>

Arguments:
  <PATTERN>  a regex pattern to search for
  <PATH>     path in which to search recursively

Options:
  -I, --ignore-paths <IGNORE_PATHS>  paths to ignore when recursively walking target directory
  -G, --respect-gitignore            respect .gitignore when recursively walking directory
  -M, --max-results <MAX_RESULTS>    upper boundary for the number of results to expect (will panic if #results > max_results) [default: 1000]
  -T, --n-threads <N_THREADS>        number of threads to use [default: 4]
  -U, --multiline                    enable multiline matching
      --json                         output in JSON format
  -f, --file-paths-only              output file paths only
  -h, --help                         Print help
  -V, --version                      Print version

```
