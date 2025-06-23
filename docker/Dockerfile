FROM instrumentisto/flutter:latest

# Install required packages
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    git \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# Accept Android SDK licenses
RUN yes | flutter doctor --android-licenses

# Pre-install Android SDK components
RUN sdkmanager --install "build-tools;34.0.0" \
    "ndk;26.3.11579264" \
    "cmake;3.22.1"

RUN flutter precache && flutter pub get

# Set environment variables for Gradle
#ENV GRADLE_OPTS="-Dorg.gradle.daemon=true -Dorg.gradle.parallel=true -Dorg.gradle.caching=true -Dorg.gradle.configureondemand=true"

# Create a volume for Gradle cache
#VOLUME /root/.gradle