# ollama
Ollama Test

curl -fsSL https://ollama.com/install.sh | sh

ollama run gemma:7b

lxuser@scanf:~$ ollama run gemma:7b
pulling manifest 
pulling 456402914e83... 100% ▕███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████▏ 5.2 GB                         
pulling 097a36493f71... 100% ▕███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████▏ 8.4 KB                         
pulling 109037bec39c... 100% ▕███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████▏  136 B                         
pulling 22a838ceb7fb... 100% ▕███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████▏   84 B                         
pulling a443857c4317... 100% ▕███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████▏  483 B                         
verifying sha256 digest 
writing manifest 
removing any unused layers 
success 
Error: Post "http://127.0.0.1:11434/api/chat": EOF



export GOLANG_VERSION=1.21.3
export GO_ARCH=arm64
export CMAKE_VERSION=3.22.1
export LD_LIBRARY_PATH=/usr/local/cuda/lib:/usr/local/cuda/lib64/:/usr/local/cuda/include
export OLLAMA_SKIP_CPU_GENERATE="1"
export CGO_ENABLED="1"
export CMAKE_CUDA_ARCHITECTURES="72;87"


Ensure required tools are installed
sudo apt update && sudo apt install -y build-essentials
curl -s -L https://github.com/Kitware/CMake/releases/download/v${CMAKE_VERSION}/cmake-${CMAKE_VERSION}-linux-$(uname -m).tar.gz | tar -zx -C /usr --strip-components 1
rm /usr/local/bin/cmake && update-alternatives --install /usr/local/bin/cmake cmake /usr/bin/cmake 30
curl -s -L https://dl.google.com/go/go${GOLANG_VERSION}.linux-${GO_ARCH}.tar.gz | tar xz -C /usr/local
ln -s /usr/local/go/bin/go /usr/local/bin/go
ln -s /usr/local/go/bin/gofmt /usr/local/bin/gofmt


Clone repo and build. Ensure you first cd <project folder>

git clone https://github.com/ollama/ollama.git && cd ollama
go clean
go generate ./… && go build .
