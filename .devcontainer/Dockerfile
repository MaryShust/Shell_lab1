FROM ubuntu:jammy  # Используем актуальную LTS версию Ubuntu

# Устанавливаем базовые зависимости
RUN apt-get update && apt-get install -y 
    curl 
    git 
    cmake 
    clang 
    clangd 
    clang-tidy 
    clang-format 
    lldb 
    sudo 
    && rm -rf /var/lib/apt/lists/*

# Устанавливаем Node.js (требуется для VSCode Remote Containers)
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - 
    && apt-get install -y nodejs

# Создаём не-root пользователя (рекомендуется для VSCode)
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN groupadd --gid $USER_GID $USERNAME 
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME 
    && echo $USERNAME ALL=(root) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME 
    && chmod 0440 /etc/sudoers.d/$USERNAME

USER $USERNAME
