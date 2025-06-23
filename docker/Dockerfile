FROM debian:bookworm-slim

# Install system dependencies for Flutter Web/Linux
RUN apt-get update && apt-get install -y --no-install-recommends \
  curl \
  git \
  unzip \
  xz-utils \
  zip \
  ca-certificates \
  build-essential \
  clang \
  cmake \
  ninja-build \
  pkg-config \
  libgtk-3-dev \
  libglib2.0-dev \
  libgstreamer1.0-dev \
  libgstreamer-plugins-base1.0-dev \
  && rm -rf /var/lib/apt/lists/*

# Set environment variables
ENV FLUTTER_VERSION=3.22.1 \
    FLUTTER_HOME=/opt/flutter

# Install Flutter SDK (Web + Linux support included)
RUN git clone --depth 1 --branch $FLUTTER_VERSION https://github.com/flutter/flutter.git $FLUTTER_HOME

ENV PATH="$FLUTTER_HOME/bin:$FLUTTER_HOME/bin/cache/dart-sdk/bin:$PATH"

# Precache tools
RUN flutter precache --web --linux && flutter doctor -v

# Set working directory
WORKDIR /app

# Optional: uncomment to copy and resolve pub dependencies during image build
# COPY pubspec.* ./
# RUN flutter pub get

# This image expects app volume mounting, so no CMD